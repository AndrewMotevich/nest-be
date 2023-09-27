# Nest-be
This is my nest backend for project Cv-gen. Its allow you to manipulate data in three coolections: cvs, projects, employees.

## Run api
1. Install docker
2. Run Api by docker compose
```
docker-compose up
```


***

### **API** starts on http://localhost:3000/api

### **SWAGER** starts on http://localhost:3000/docs

### **PgAdmin** starts on http://localhost:5050

Credentials for pgAdmin (see compose.yaml):
  - PGADMIN_DEFAULT_EMAIL: "admin@admin.com"
  - PGADMIN_DEFAULT_PASSWORD: "Admin1234"

## FAQ
<details>
<summary>Before usage!!! Add user.</summary>
Before usage you should add an admin or first user in tab USERS
To add user => post user credentials
After adding you can Authorize.
</details>
<details>
<summary>How to authorize?</summary>
NOTE: Add user before authorize!
To get access you should use Authorize button in swagger or Authorization="Bearer <'your-access-token>" header in http request.
</details>
<details>
<summary>Difference between scheme with Dto suffix and without it?</summary>
Scheme with Dto suffix used to pass data to the api. Dto is a 'data transfer object'. These schemas are using for POST and PATCH methods
Schemes without Dto are outputs from GET methods
</details>
<details>
<summary>PUT vs PATCH?</summary>
I used PUT, because, we should update sub-collections like skills and ect.
PATCH rewrite single fields and add additional data to collection. For instance, you can add new skills, but can't delete unnecessary!
Note!!! Each PUT rewrite all data!
</details>
<details>
<summary>Can't add new Cv (employeeId)?</summary>
'employeeId' field is necessary for relation between employee and cv.
You cant add cv without relation to employee. Please, check 'employeeId' property if something goes wrong!
</details>
<details>
<summary>All types of errors in the project!</summary>
Note: Every time read error message! That can help you to resolve a problem.
400 Bad request Error. Check you body or parameters!
401 Unauthorized Error. Happened if you haven't got an access-token or have incorrect token. You should log-in/sign-in or refresh tokens!
403 Forbidden Error. Happened if credentials or refresh-token are incorrect. Check credentials and re log-in!
404 Not found Error. Happened if entity isn't exist. Check your id.
500 Internal server Error. This error will arrive if I couldn't handle error. See message to resolve it.
</details>
