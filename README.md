# Instruction

## 1. Setting up the app

### 1.1 Set up Auth0
1. Log in to [Auth0](https://manage.auth0.com/)

2. Go to Getting Started > Create Application > choose `Regular Web Applications` > Create > choose `Python`

3. Go to Settings, you should be able to see the following in Bacsic information:
    - Domain (`dev-g*********z.us.auth0.com`)
    - Client ID (`1********************R`)
    - Clinet Secret (`A*********************************************4`)

4. Then scroll down to locate Application URIs, and fill in the following field:
    - Allowed Callback URLs: `http://localhost:3000/callback`
    - Allowed Logout URLs: `http://localhost:3000`
    - Allowed Web AOrigins: `http://localhost:3000`

Then click `Save Changes` Button to save your change.

> [!IMPORTANT]  
> If you encounter error indicating you did not have the call back url set up at the last step, please check if your server is running on `127.0.0.1` instead of `localhost`. You can also add `http://127.0.0.1:3000` into allowed URLs, you will need to seperate two URLs by adding `,` between them.


### 1.2 Install dependencies
1. Create an empty folder, at root level, create a `requirements.txt` file with the following content:
```txt
# 📁 requirements.txt -----

flask>=2.0.3
python-dotenv>=0.19.2
authlib>=1.0
requests>=2.27.1
```

2. In your terminal, run `pip install -r requirements.txt`, if you want to use venv for your python, please use `python -m venv venv && source venv/bin/activate` before you run `pip install`.

### 3. Configure `.env` file
1. Create a `.env` file at the root directory, and fill in the keys you get from Step 1.

```env
# 📁 .env -----

AUTH0_CLIENT_ID=your_client_id_here
AUTH0_CLIENT_SECRET=your_client_secret_here
AUTH0_DOMAIN=your_domain_here
APP_SECRET_KEY=
```

2. for the `APP_SECRET_KEY`, please use command `openssl rand -hex 32` to generate one. You should get an output looks like `bc***********************************408`

### 4. Examine the code:
Please examine the project structure below, make sure all essential files exist
```
.
├── server.py              # Main Flask application with Auth0 integration
├── templates/            # HTML templates foler
│   ├── home.html        # Home page template
│   └── protected.html   # Protected page template
└── .env                 # Environment variables
```

### 5. Run the application:
run command `python3 server.py`