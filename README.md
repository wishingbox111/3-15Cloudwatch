# 3-15Cloudwatch


-see Coaching.pptx

- git clone
- npm init * right after git clone
- npm install serverless * don't need this?
- npm install serverless-offline –save-dev * i think is after putting index.js and serverless.yml without the environment in serverless.yml yet

- Had to install serverless again at serverless plugin install -n serverless-offline

After installation then it seems to work.

- serverless deploy #to deploy serverless application *check that lambda is added under your service name
- serverless remove #to remove serverless application on lambda
- .gitignore (add node_modules/ and .serverless)




--------------------------------------------

secret manager's code:

// Use this code snippet in your app.
// If you need more information about configurations or implementing the sample
// code, visit the AWS docs:
// https://docs.aws.amazon.com/sdk-for-java/latest/developer-guide/home.html

// Make sure to import the following packages in your code
// import software.amazon.awssdk.regions.Region;
// import software.amazon.awssdk.services.secretsmanager.SecretsManagerClient;
// import software.amazon.awssdk.services.secretsmanager.model.GetSecretValueRequest;
// import software.amazon.awssdk.services.secretsmanager.model.GetSecretValueResponse;	

public static void getSecret() {

    String secretName = "chen-Secret";
    Region region = Region.of("ap-southeast-1");

    // Create a Secrets Manager client
    SecretsManagerClient client = SecretsManagerClient.builder()
            .region(region)
            .build();

    GetSecretValueRequest getSecretValueRequest = GetSecretValueRequest.builder()
            .secretId(secretName)
            .build();

    GetSecretValueResponse getSecretValueResponse;

    try {
        getSecretValueResponse = client.getSecretValue(getSecretValueRequest);
    } catch (Exception e) {
        // For a list of exceptions thrown, see
        // https://docs.aws.amazon.com/secretsmanager/latest/apireference/API_GetSecretValue.html
        throw e;
    }

    String secret = getSecretValueResponse.secretString();

    // Your code goes here.
}