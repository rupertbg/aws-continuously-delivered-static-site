# Example: Continuously Delivered Static Site on AWS
This example repo deploys a HostedZone via `domain.yml` and a Pipeline via `pipeline.yml`. The Pipeline deploys itself, `infra.yml` and a folder called `src` into a non-public S3 Bucket. `infra.yml` contains a CloudFront Distribution mapped to the S3 Bucket, and the associated RecordSets and Certificate.

## Usage
You can use the included HostedZone template to spin up the DNS for your domain if you haven't done this already. If you already have a HostedZoneId you can use, skip this step.

  1. [Optional] Deploy `domain.yml` via CloudFormation to create a HostedZone for your domain.
  2. Generate a [Personal Access Token](https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line) for Github and store it in [Secrets Manager](https://aws.amazon.com/secrets-manager/).
  2. Deploy `pipeline.yml` via CloudFormation.
  3. Go to CodePipeline to watch your site deploy itself.
  4. During the first Cloudfront deployment step an ACM Certificate will be created. Check the ACM Console during this step to validate the certificate.
