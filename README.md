# My Daily Dashboard - A Personal Productivity App

My Daily Dashboard is a single-page web application designed to help users organize their day, track their progress, and build consistent habits. Built with modern web technologies, it provides a clean, interactive, and personalized interface for managing daily routines.

The application allows users to create a permanent account, customize their daily schedule, mark tasks as complete, and visualize their progress over time, ensuring all data is securely synced across devices.

## ✨ Key Features

* **Secure User Authentication:** Users can sign up and log in with an email and password. All data is tied to their personal account.
* **Fully Customizable Routine:** An intuitive interface to add, edit, or delete tasks from your daily schedule. You can set the time, activity, goal, and category for each task.
* **Interactive Timeline:** A visual, chronological view of your day. The current task is highlighted, and future tasks are clearly distinguished.
* **Real-time Progress Tracking:**
    * **Task Checkmarks:** Mark tasks as complete with a satisfying checkmark. Progress is saved instantly.
    * **Progress Bar:** A visual bar at the top shows how far you are through your day.
    * **Completion Counter:** See at a glance how many tasks you've completed (`X / Y`).
* **Progress History & Analytics:**
    * Click "View History" to see your performance over time.
    * A line chart visualizes your task completion percentage for the last 30 days.
    * An interactive calendar shows a color-coded daily summary. Click any day to see the exact tasks you completed.
* **Smart Daily Reset:** The app automatically archives the previous day's progress and gives you a fresh, clean slate every morning. You never lose your history.
* **Motivational Focus Tips:** Get a random, uplifting quote to start your day with the right mindset.
* **100% Free to Host & Use:** Built with a tech stack that allows for completely free hosting on platforms like Netlify or Vercel.

## 🛠️ Tech Stack

* **Frontend:** HTML5, CSS3, JavaScript (ES6 Modules)
* **Styling:** [Tailwind CSS](https://tailwindcss.com/)
* **Data Visualization:** [Chart.js](https://www.chartjs.org/)
* **Backend & Database:** [Google Firebase](https://firebase.google.com/)
    * **Firestore Database:** For storing user schedules and history data.
    * **Firebase Authentication:** For secure email/password sign-up and login.

## 🚀 Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

* A code editor (e.g., [VS Code](https://code.visualstudio.com/))
* A web browser
* A free [Firebase](https://firebase.google.com/) account

### Installation & Setup

1.  **Clone the Repo (or save the `index.html` file):**
    If this were a Git repository, you would clone it. For this project, simply save the provided `index.html` file to a folder on your computer.

2.  **Create a Firebase Project:**
    * Go to the [Firebase Console](https://console.firebase.google.com/) and create a new project.
    * Inside your new project, go to the **Authentication** section, click the "Sign-in method" tab, and **enable** the **Email/Password** provider.
    * Go to the **Firestore Database** section, click "Create database," start in **production mode**, and choose a location. Then, go to the **Rules** tab and replace the default rules with the following to allow users to access their own data:
        ```
        rules_version = '2';
        service cloud.firestore {
          match /databases/{database}/documents {
            match /artifacts/{appId}/users/{userId}/{document=**} {
              allow read, write: if request.auth != null && request.auth.uid == userId;
            }
          }
        }
        ```
    * Publish the new rules.

3.  **Get Your Firebase Config Keys:**
    * In your Firebase project settings (click the ⚙️ icon), scroll down to "Your apps."
    * Click the web icon (`</>`) to create a new web app.
    * Give it a nickname and click "Register app."
    * Copy the `firebaseConfig` object.

4.  **Add Your Keys to the Code:**
    * Open the `index.html` file in your code editor.
    * Find the `firebaseConfig` object within the `<script type="module">` tag.
    * Replace the placeholder values with the keys you just copied from your Firebase project.

5.  **Run the App:**
    You can now open the `index.html` file directly in your web browser to use the application locally.

## 🌐 Deployment

This application is ready to be deployed to any static site hosting service.

1.  **Choose a Host:** Free options like [Netlify](https://www.netlify.com/), [Vercel](https://vercel.com/), or [GitHub Pages](https://pages.github.com/) are excellent choices.
2.  **Deploy:** Most services offer a simple drag-and-drop interface where you can upload your `index.html` file.
3.  **Authorize Your Domain:** **This is a critical final step!**
    * Go back to your Firebase project's **Authentication** settings.
    * Click the **Settings** tab.
    * Under **Authorized domains**, click "Add domain" and enter the live URL provided by your hosting service (e.g., `your-awesome-app.netlify.app`).

Your Daily Dashboard is now live and fully functional for you and anyone else to use!
