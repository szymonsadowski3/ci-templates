# java-gradle-setup

This action runs Junit tests, publishes the test results and tests signing for Sonatype.

## Input Parameters

If you do not set input parameters for publishing code quality test results on Sonarcloud or for testing the signing for
Sonatype, then these steps are skipped.

| Name                    | Required | Default Value |  Type   | Description                                                                                                   |
| ----------------------- | :------: | :-----------: | :-----: | ------------------------------------------------------------------------------------------------------------- |
| sonar-token             |    ❌    |       -       | string  | Token for Sonarcloud                                                                                          |
| sonar-organization      |    ❌    |       -       | string  | Organization for Sonarcloud                                                                                   |
| signing-secret-key-ring |    ❌    |       -       | string  | Key ring (base64 encoded) for signing the Sonatype publication                                                |
| signing-key-id          |    ❌    |       -       | string  | Key id for signing the Sonatype publication                                                                   |
| signing-password        |    ❌    |       -       | string  | Password for signing the Sonatype publication                                                                 |
| java-distribution       |    ❌    |   microsoft   | string  | [Java distribution](https://github.com/actions/setup-java#supported-distributions) to be installed            |
| java-version            |    ❌    |      11       | string  | Java version to be installed                                                                                  |
| gradle-version          |    ❌    |    wrapper    | string  | [Gradle version](https://github.com/gradle/gradle-build-action#use-a-specific-gradle-version) to be installed |
| gradle-cache            |    ❌    |     true      | boolean | Whether Gradle caching is enabled or not                                                                      |
| working-directory       |    ❌    |      "."      | string  | Working directory of your Gradle artifacts                                                                    |

## Usage

```yaml
steps:
  - name: Test
    uses: bakdata/ci-templates/actions/java-gradle-test@main
    with:
      sonar-token: ${{ secrets.sonar-token }} # (Optional) If not set, code quality tests are skipped
      sonar-organization: ${{ secrets.sonar-organization }} # (Optional) If not set, code quality tests are skipped
      signing-secret-key-ring: ${{ secrets.signing-secret-key-ring }} # (Optional) If not set, signing for Sonatype is not tested
      signing-key-id: ${{ secrets.signing-key-id }} # (Optional) If not set, signing for Sonatype is not tested
      signing-password: ${{ secrets.signing-password }} # (Optional) If not set, signing for Sonatype is not tested
      java-distribution: "microsoft" # (Optional)
      java-version: "11" # (Optional)
      gradle-version: "wrapper" # (Optional)
      working-directory: "." # (Optional)
```
