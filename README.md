# WeatherWebApi
ASP .NET Core web api to register , login , view profile and call external weather data

### build local
dotnet restore
dotnet build
dotnet run

appsettings.development.json contains the input for AWSSecretAccessKey , AWSKeyId , AWSBucketName, SecretKey and WeatherApiKey.
These are left empty by default, to be entered manually during development ,during deployment supplied via env variables.  


## Environment variables
| Name                           | Required (yes/no) | Default value                                                            | Description        |
| ------------------------------ | ----------------- | -------------------------------------------------------------------------| ------------------ |
| DbConnection                   | yes               | server=127.0.0.1;port=3306;uid=root;pwd=password;database=mydb(local dev)| DbConnectionString |
| AWSSecretAccessKey             | yes               | none                                                                     | AWSSecretAccessKey |
| AWSKeyId                       | yes               | none                                                                     | AWSKeyId           |
| AWSBucketName                  | yes               | none                                                                     | AWSBucketName      |
| SecretKey                      | yes               | none                                                                     | SecretKey          |
| WeatherApiKey                  | yes               | none                                                                     | WeatherApiKey      |

## ⚙️ Deployment
Build Docker Image
```lang-bash
docker build -t weatherapi .
```
Run Docker Image (with env variables)
```lang-bash
docker run -p 5005:5005 --env DbConnection="server=host.docker.internal;port=3306;uid=root;pwd=password;database=testdb" --env AWSKeyId="<enter key here>" --env AWSSecretAccessKey="<enter key here>" --env AWSBucketName="<enter key here>" --env SecretKey="<>" --env WeatherApiKey="<>" --name weatherapi weatherapi
```

The project contains Postman Collection Tests file and can also be tested via Swagger -> http://localhost:5005/swagger/html
