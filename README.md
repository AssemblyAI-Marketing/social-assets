# social-assets

Public image host for AssemblyAI social posts. Buffer only accepts post media by public URL, so the
`social-drafter` plugin (in `AssemblyAI/aai-cc-plugins`) uploads each post's image here and hands Buffer the
`raw.githubusercontent.com` link.

**Everything in this repo is public the moment it's pushed.** Don't upload anything under embargo, customer
data, or internal-only material. Upload a post's image only once its copy is approved for a Buffer draft.

## Layout

```
YYYY/MM/<file-name>-<8-char content hash>.<ext>
```

Files are named by a hash of their contents, so uploading the same image twice reuses the existing file.

## Uploading

Use the Buffer skill in social-drafter:

```
node scripts/buffer.mjs media:upload <path-to-image>
node scripts/buffer.mjs posts:create --channel linkedin --file copy.txt --image-file chart.png
node scripts/buffer.mjs posts:update <post_id> --image-file chart.png
```

It needs `gh` signed in as a member of the AssemblyAI-Marketing org with write access to this repo.

Supported: PNG, JPEG, GIF and WebP, up to 20 MB each. Video still gets attached by hand in Buffer.
