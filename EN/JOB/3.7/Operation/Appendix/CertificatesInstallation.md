# Certificate installation

Assuming that the current certificate storage location is **/data/enterprise/certs,** decompress ssl_certificates.tar.gz file list
```bash
job_server.key job API server certificate and key file
job_server.crt job API server certificate file
job_ca.key job API server root certificate key file
job_ca.crt job API server root certificate file
gseca.crt Server root certificate file for GSE
gse_job_api_client.p12 Certificate file in p12 format provided by GSE to JOB
pass.txt The file that saves the password of each certificate is used to provide the operation script to initialize the configuration file
```

## Certificate installation for connecting to GSE
### Generate keystore file

```bash
keytool -importkeystore -v -srckeystore gse_job_api_client.p12 -srcstoretype pkcs12 -destkeystore gse_job_api_client.keystore -deststoretype jks -srcstorepass keystore password -deststorepass keystore password -noprompt
```

**illustrate:**

**gse_job_api_client.keystore**: The storage file for the JOB to connect to the GSE API client certificate and key

**keystore password**: Obtained from the pass.txt file, the password of gse_job_api_client.p12


### Generate truestore file
```bash
keytool -keystore gse_job_api_client.truststore -alias ca -import -trustcacerts -file gseca.crt -storepass truststore password -noprompt
```
illustrate:

**gse_job_api_client.truestore**: Provide JOB to connect to GSE API trust server certificate store file

**truststore password**: As the generated truststore file password, it is recommended to be consistent with the keystore file password, scheme management

## JOB API Server certificate installation

This certificate is used for security authentication of clients (such as ESB) connecting to the JOB API interface

### Generate JOB API keystore file
```bash
keytool -importkeystore -v -srckeystore job_server.p12 -srcstoretype pkcs12 -destkeystore job_server.keystore -deststoretype jks -srcstorepass keystore password -deststorepass keystore password -noprompt
```

**illustrate**:

**job_server.keystore**: Store file of JOB API server certificate and key

**keystore password**: Obtain the job_server.key password from the pass.txt file as the generated keystore file password

### Generate JOB API truestore file

```bash
keytool -keystore job_server.truststore -alias ca -import -trustcacerts -file job_ca.crt -storepass truststore password -noprompt
```

**illustrate:**

**job_server.truststore**: JOB root server trust certificate store file

**truststore password**: As the generated truststore file password, it is recommended to be consistent with the keystore file password, plan management.