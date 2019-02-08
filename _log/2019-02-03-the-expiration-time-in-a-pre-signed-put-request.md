---
title: The expiration time in a pre-signed PUT request
date: 2019-02-03 05:03:00 +0100
subtitle: 3rd February, 2019
categories: Logs
tags: [log]
---

Today I learned this thing since I've realized S3 doesn't allow to upload some large files using the pre-signed method to upload files from the client to S3 without passing 'GO'.

The issue was caused by the expiration time which is the duration of the token generated by S3. That time can be configured in the S3 object such as:

```javascript
const s3Params = {
    Bucket: S3_BUCKET,
    Key: pathName,
    Expires: 60 * 15,
    ContentType: fileType,
    ACL: 'public-read'
}
```

Increasing (in seconds) this parameter in the `S3 config object` sorted my issue.