+++
title = "GetConfigurationValue"
toc = true
+++

Retrieve a System Configuration Value.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "GetConfigurationValue" | Required |
| setting | string | The name of the setting to be obtained | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| setting | string | The setting name |
| value | string | The setting value |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'GetConfigurationValue',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'setting' => 'SystemURL',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'GetConfigurationValue';
$postData = array(
    'setting' => 'SystemURL',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "setting": "SystemURL",
    "value": "http:\/\/www.example.com\/whmcs\/"
}
```


### Error Responses

Possible error condition responses include:

* Parameter setting is required
* Invalid name for parameter setting


### Version History

| Version | Changelog |
| ------- | --------- |
| 7.0.0-beta.1 | Initial Version |
