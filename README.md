
def create_db_connection(db='facetsdb', env='test'):
    print(f"Starting database connection setup for {db.upper()} in {env.upper()} environment")
    
    # Construct key names
    url_key = f"{db.upper()}_{env.upper()}_DB_URL"
    pwd_key = f"{db.upper()}_{env.upper()}_DB_USERPWD"
    print(f"Constructed keys - URL: {url_key}, Password: {pwd_key}")
    
    try:
        # Load YAML config file
        print("Loading db_config.yaml file...")
        with open('db_config.yaml', 'r') as file:
            db_config = yaml.safe_load(file)
            db_url = db_config[db][url_key]
            print(f"Found DB URL: {db_url}")
    except Exception as e:
        print(f"Error reading db_config.yaml: {str(e)}")
        return None
    
    try:
        # Load .envpwd file
        print("Loading .envpwd file...")
        load_dotenv('envpwd')  # Load environment variables from file
        db_userpwd = os.getenv(pwd_key)
        if not db_userpwd:
            raise ValueError(f"Password not found for key {pwd_key}")
        print("Password retrieved successfully (masked for security)")
    except Exception as e:
        print(f"Error reading .envpwd file: {str(e)}")
        return None
    
    try:
        # Split username and password
        username, password = db_userpwd.split('/')
        print(f"Extracted username: {username}")
        
        # Simulate database connection
        print(f"Attempting to connect to {db_url} with username {username}...")
        # Here you would put your actual connection code
        # connection = create_actual_connection(db_url, username, password)
        
        print("Connection established successfully!")
        return {
            'status': 'success',
            'db_url': db_url,
            'username': username,
            'password': '********'  # Masked for security
        }
    except Exception as e:
        print(f"Connection failed: {str(e)}")
        return None

# Example usage
if __name__ == "__main__":
    connection = create_db_connection(db='facetsdb', env='test')
    print("\nFinal connection details:")
    print(connection)
