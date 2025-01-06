# ✨ Screen Capture + AI Analysis & Chat

Welcome to an interactive application that empowers you with screen capture, annotation, and intelligent AI analysis. This project not only captures your screen but also allows you to highlight, annotate, and engage with an AI assistant, all while maintaining aspect ratios perfectly. Let's explore how this works!


## 🎯 Key Features

-   **📸 Real-time Screen Capture:** Effortless, high-quality screen captures.
-   **✂️ Precise Sub-Selection:** Select any region with precision using our intuitive click-and-drag tool.
-   **✍️ Versatile Annotation Tools:** Mark up your captures with freehand lines, shapes, and text.
-   **🧽 Intuitive Eraser:** Correct your annotations with our eraser tool.
-   **↩️ & ↪️ Undo/Redo:** Easily step back or forward in your annotation history.
-   **🧹 Clear Canvas:** Quickly reset and start anew.
-   **🧠 AI-Powered Insights:** Let our AI analyze and provide intelligent textual responses.
-   **💬 Interactive Chat:** Engage the AI assistant in a real-time chat.
-   **📝 Dynamic Documentation:** Generate comprehensive documentation from your annotated captures.
-    **🔍 Contextual Shape Analysis:** Right-click on any closed shape to get an explanation.
-   **📐 Aspect Ratio Mastery:** Captures and canvas maintain correct aspect ratios.
-   **Responsive Design:** Works perfectly on different screen sizes and devices.

## 🎬 Demo

![image](https://github.com/user-attachments/assets/423f2abf-2ea1-4a4d-9632-62ff0e565679)

![image](https://github.com/user-attachments/assets/ff8d5e56-7eb7-4c4a-889e-3823f26e9d04)

![image](https://github.com/user-attachments/assets/ded8a979-6493-4b76-b10a-30fb0f8a2fd4)

![image](https://github.com/user-attachments/assets/e726a6f2-4ba1-43a4-b7f1-4ce6a0138883)


## 🛠️ Getting Started

Follow these steps to get the application running on your local machine:

### 1. Backend Setup - Python Server 🐍

1.  **Install Dependencies:** Use `pip` to install required Python packages:

    ```bash
    pip install Flask python-dotenv
    ```

2.  **Create `.env` File:** Create a `.env` file and add your OpenAI API key, replacing `YOUR_OPENAI_API_KEY_HERE`:

    ```
    OPENAI_API_KEY=YOUR_OPENAI_API_KEY_HERE
    ```

    ⚠️ **Important:** Protect your API key! Do not commit this file to your version control.

3.  **Create `app.py`:** Create your `app.py` using the code below. Make sure to keep it in the same directory as `.env`.

    ```python
    from flask import Flask, jsonify
    from flask_cors import CORS
    import os
    from dotenv import load_dotenv

    load_dotenv()
    openai_api_key = os.getenv("OPENAI_API_KEY")

    app = Flask(__name__)
    CORS(app)

    @app.route("/")
    def get_api_key():
        return jsonify({"access_token": openai_api_key})

    if __name__ == "__main__":
        app.run(port=3000, debug=True)
    ```

4.  **Run the Server:** Start your Flask server:

    ```bash
    python app.py
    ```

    Your server is now active at `http://localhost:3000`.

### 2. Frontend Setup - HTML Application 🖥️

1.  **Save HTML:** Take the HTML/CSS/JavaScript code and save it as `index.html`.
2.  **Serve the HTML:** Start a local server from the directory containing your `index.html` using:

    ```bash
    python -m http.server
    ```

    Access the application through `http://localhost:8000` or `http://127.0.0.1:8000`.

    💡 **Pro Tip:** The frontend fetches the API key from `http://localhost:3000`. Ensure both servers are running concurrently.

## 🕹️ Usage Guide

1.  **Start Screen Capture:** Click the "Start Screen Capture" button.
2.  **Select a Region:** Click and drag to select a part of your screen.
3.  **Annotate:** Click "Start Edit Mode" to add your own notes with shapes, lines, and text.
4.  **Engage AI:** Use the chat interface to send messages to the AI.
5.  **Documentation:** Click on "Create Documentation" to have the AI create step-by-step document of your capture.
6.  **Context Menu:** Right-click on a closed shape to get explanation on the selected shape.
7.  **Chat:** Use the text box on the right to communicate with the AI assistant.

## 🛠️ Technologies

-   **Frontend:** HTML, CSS, JavaScript
-   **Backend:** Python (Flask)
-   **AI:** OpenAI API

## 🤝 Contributing

We welcome contributions from the community!


## 🌟 Support

If you find this project useful, give it a star on GitHub!

## 🐛 Report a Bug

Encountered a bug? Please submit it as an issue in our issue tracker on Github!
