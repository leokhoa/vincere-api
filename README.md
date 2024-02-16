# vincere-api
Call vincere-api
# Get Code:
# Need to open in browser:
# The callback URL must match
# client_id: the client_id of the tenant bi-sandbox.vincere.io

1. Generate ID Token (Open in the browser:)
https://id.vincere.io/oauth2/authorize?client_id=d2130f76-3cbf-437d-b1a3-22fbc95d031b&state=STATE&redirect_uri=https://nothing.abc&response_type=code

response_type   string  This must be the code
client_id       string  This is the client id provided by Vincere Support
redirect_uri    string  This is the callback url you provide
state   string  Any urlencoded string to pass along to the callback url to track state within the client app

2. Authentication
https://(callback url)?code=(authorization code)&state=STATE
-> https://nothing.abc/?code=78184525-f2cc-452e-bdb8-681fd6a1523f&state=STATE
3. Authorization
curl --location --request POST 'https://id.vincere.io/oauth2/token?client_id=d2130f76-3cbf-437d-b1a3-22fbc95d031b&grant_type=authorization_code&code=CODE' \
--header 'Content-Type: application/x-www-form-urlencoded'

Parameter       Value   Remarks
client_id       string  This is the client id provided by Vincere Support
code    string  This is the callback url you provide
grant_type      string  The value must be set as authorization_code



-----------
 cat 2.search-candidates.sh
curl --location 'https://bi-sandbox.vincere.io/api/v2/candidate/search/fl=id,name,first_name' \
--header 'id-token: eyJraWQiOiI5bHNyUXBsU1lXWDNXXC9CR0o1UjZWUzFKVmp3TjNMYUtyWjg5NTdMXC9UZlU9IiwiYWxnIjoiUlMyNTYifQ.eyJhdF9oYXNoIjoiLWt4ZkFhRkZjVENIOC1yaGtYeHl0USIsInN1YiI6ImFiNjJmN2NjLTA5N2UtNDk5Yi1hOGUwLTJkNzhiNzJhY2JlNCIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJpc3MiOiJodHRwczpcL1wvY29nbml0by1pZHAudXMtZWFzdC0xLmFtYXpvbmF3cy5jb21cL3VzLWVhc3QtMV9ERnNRcDdtN0QiLCJwaG9uZV9udW1iZXJfdmVyaWZpZWQiOnRydWUsImNvZ25pdG86dXNlcm5hbWUiOiJhYjYyZjdjYy0wOTdlLTQ5OWItYThlMC0yZDc4YjcyYWNiZTQiLCJhdWQiOiI3YnM4MDBjZ2diZWxjNjgxdXU1MTc1b2tibyIsInRva2VuX3VzZSI6ImlkIiwiYXV0aF90aW1lIjoxNzA4MDg2NTA4LCJwaG9uZV9udW1iZXIiOiIrODQxMjU0MzM3NDY3IiwiZXhwIjoxNzA4MDkwMTA4LCJpYXQiOjE3MDgwODY1MDgsImVtYWlsIjoic3lzYWRtaW5AdmluY2VyZS5pbyJ9.bDC-sSr6lhCuoQkygCybS6VTcQqd7TQJI4_7mHm36lJyfd3EHqWWnuRjdZPoq4tZGqQn5xKuxxBq9SiZ_MbBdZT_qVwrwqdvKeRxpgv-OkXyvFEAYa7auKzD53KVoE5bKE07Euq2-xaLxKjODXsVfBN5HKmXuRK0yqOtFu9TWXlbxRCnfUPzE-OPVL_bdZ4wUIP7GhEKdFxpvh0E7BannGgu5OL6uha5IDuTHJ9N7jJZAXs-T6SEHc2oiUsRHw-ktFakJDUElE8MB1AwCov1XtNWNEHNLV3TM6XEbPkZgOlQHGVIaXUdup1WSA8zE52qAJc04l3pRxDlwK_L2Djm-Q' \
--header 'x-api-key: 894eb57b57043c4c3a838132e9f3ea24'


-----------
 cat 3.get-a-candidate-details.sh
curl --location 'https://bi-sandbox.vincere.io/api/v2/candidate/62818' \
--header 'id-token: eyJraWQiOiI5bHNyUXBsU1lXWDNXXC9CR0o1UjZWUzFKVmp3TjNMYUtyWjg5NTdMXC9UZlU9IiwiYWxnIjoiUlMyNTYifQ.eyJhdF9oYXNoIjoiLWt4ZkFhRkZjVENIOC1yaGtYeHl0USIsInN1YiI6ImFiNjJmN2NjLTA5N2UtNDk5Yi1hOGUwLTJkNzhiNzJhY2JlNCIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJpc3MiOiJodHRwczpcL1wvY29nbml0by1pZHAudXMtZWFzdC0xLmFtYXpvbmF3cy5jb21cL3VzLWVhc3QtMV9ERnNRcDdtN0QiLCJwaG9uZV9udW1iZXJfdmVyaWZpZWQiOnRydWUsImNvZ25pdG86dXNlcm5hbWUiOiJhYjYyZjdjYy0wOTdlLTQ5OWItYThlMC0yZDc4YjcyYWNiZTQiLCJhdWQiOiI3YnM4MDBjZ2diZWxjNjgxdXU1MTc1b2tibyIsInRva2VuX3VzZSI6ImlkIiwiYXV0aF90aW1lIjoxNzA4MDg2NTA4LCJwaG9uZV9udW1iZXIiOiIrODQxMjU0MzM3NDY3IiwiZXhwIjoxNzA4MDkwMTA4LCJpYXQiOjE3MDgwODY1MDgsImVtYWlsIjoic3lzYWRtaW5AdmluY2VyZS5pbyJ9.bDC-sSr6lhCuoQkygCybS6VTcQqd7TQJI4_7mHm36lJyfd3EHqWWnuRjdZPoq4tZGqQn5xKuxxBq9SiZ_MbBdZT_qVwrwqdvKeRxpgv-OkXyvFEAYa7auKzD53KVoE5bKE07Euq2-xaLxKjODXsVfBN5HKmXuRK0yqOtFu9TWXlbxRCnfUPzE-OPVL_bdZ4wUIP7GhEKdFxpvh0E7BannGgu5OL6uha5IDuTHJ9N7jJZAXs-T6SEHc2oiUsRHw-ktFakJDUElE8MB1AwCov1XtNWNEHNLV3TM6XEbPkZgOlQHGVIaXUdup1WSA8zE52qAJc04l3pRxDlwK_L2Djm-Q' \
--header 'x-api-key: 894eb57b57043c4c3a838132e9f3ea24'


