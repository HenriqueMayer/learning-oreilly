#### Environments Variables

- E.g., In the application code:
    ```python
    import os
    from flask import Flask

    app = Flask(__name__)

    # ...
    # ...

    color = "red"

    
    @app.route('/')
    def home():
        print(color)
        return render_template('index.html', color=color)

    if __name__ == '__main__':
        app.run(host='0.0.0.0')
    ``` 
    - This is not flexible, because if you want to change the color, you have to modify the source code and rebuild the image.
- Instead, you can use environment variables to make the application more flexible:
    ```python
    import os
    from flask import Flask

    app = Flask(__name__)

    color = os.getenv("APP_COLOR", "red")  # Default to "red" if not set
    # ...
    ```
    - When running the container, you can set the environment variable using the `-e` flag:
        ```bash
        docker run -d -p 5000:5000 -e APP_COLOR=blue my_flask_app
        ```
        - This way, you can change the color without modifying the source code or rebuilding the image.