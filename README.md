# sjmayotte/route53-dynamic-dns
[![Docker Automated buil](https://img.shields.io/docker/automated/sjmayotte/route53-dynamic-dns.svg)](https://hub.docker.com/r/sjmayotte/route53-dynamic-dns) [![Docker Build Statu](https://img.shields.io/docker/build/sjmayotte/route53-dynamic-dns.svg)](https://hub.docker.com/r/sjmayotte/route53-dynamic-dns) [![FOSSA Status](https://app.fossa.io/api/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fsjmayotte%2Froute53-dynamic-dns.svg?type=shield)](https://app.fossa.io/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fsjmayotte%2Froute53-dynamic-dns?ref=badge_shield)
[![](https://images.microbadger.com/badges/image/sjmayotte/route53-dynamic-dns.svg)](https://microbadger.com/images/sjmayotte/route53-dynamic-dns "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/sjmayotte/route53-dynamic-dns.svg)](https://microbadger.com/images/sjmayotte/route53-dynamic-dns "Get your own version badge on microbadger.com")

WARNING: Work in progress!  Check back shortly for working version

Update [Amazon Route53](http://aws.amazon.com/route53/) hosted zone with current public IP address.  Alternative to Dynamic DNS services such as Dyn, No-IP, etc

## Usage
Run as a standalone program or in a Docker container.

### Docker
```
docker run --rm \
    --name route53-dynamic-dns \
    -e AWS_ACCESS_KEY_ID= \
    -e AWS_SECRET_ACCESS_KEY= \
    -e AWS_REGION= \
    -e ROUTE53_HOSTED_ZONE_ID= \
    -e ROUTE53_DOMAIN= \
    -e ROUTE53_TYPE= \
    -e ROUTE53_TTL= \
    -e SEND_EMAIL_SES= \
    -e SES_TO_ADDRESS= \
    -e SES_FROM_ADDRESS= \
    -e UPDATE_FREQUENCY= \
    -e NODE_ENV= \
    sjmayotte/route53-dynamic-dns
```

#### Environment Variables
* `AWS_ACCESS_KEY_ID` - Secret Key ID from AWS account; see: http://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/getting-started-nodejs.html
* `AWS_SECRET_ACCESS_KEY` - Secret Access Key from AWS account; see: http://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/getting-started-nodejs.html
* `AWS_REGION` - AWS Region; ex: "us-east-1"; see: http://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-region.html
* `ROUTE53_HOSTED_ZONE_ID` - AWS Route53 Hosted Zone ID
* `ROUTE53_DOMAIN` - AWS Route53 FQDN; ex: "home.example.com"
* `ROUTE53_TYPE` - AWS Route 53 record type for FQDN; ex: "A"
* `ROUTE53_TTL` - AWS Route 53 TTL in seconds for FQDN; ex: 60
* `SEND_EMAIL_SES` - Use AWS SES to send notification email. ex: true
* `SES_TO_ADDRESS` - If using AWS SES, this is to address for email; ex: admin@example.com   
* `SES_FROM_ADDRESS` - If using AWS SES, this is from address for email; ex: notification@example.com
* `UPDATE_FREQUENCY` - Frequency in Milliseconds of check to update Public IP; ex: 60000, which is every minute
* `NODE_ENV` - Always set to "Docker" when running in a container

## License
Route53 Dynamic DNS is licensed under the MIT License (https://opensource.org/licenses/MIT).  A copy of MIT License is included in this repository.


[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fsjmayotte%2Froute53-dynamic-dns.svg?type=large)](https://app.fossa.io/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fsjmayotte%2Froute53-dynamic-dns?ref=badge_large)