Script you can run on your computer in the background, to export your Safari history every 15 minutes and upload it to S3.

# How to use:

- Ensure you have `node` and `bun`
- install pm2 with `npm install -g pm2`
  To look at the data locally:

- Go to privacy & security -> Full Disk Access, and allow full disk access to `Terminal`
- Run `sudo bun run export-history-formatted.ts` (or other scripts); (need administrator access to export browsing history)

To run this in the background and upload it every hour:

- run `npm run create` to create your db and copy the result in `wrangler.toml`
- run `npx wrangler deploy` and put the domain in `.env` as `DOMAIN=Your Domain Here`
- run `pm2 start job.js --name "safari-history-tracker"`
- run `pm2 save` to ensure it reruns at restart
- run `pm2 logs safari-history-tracker` to view if it worked
