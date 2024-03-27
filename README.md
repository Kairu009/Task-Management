# task-manager
Our task-manager tool helps users manage their chores more successfully. It allows you to add new tasks, mark them as finished, alter their titles, and remove them. Tasks are displayed in a list manner, with the task title and a tick for marking them as done. Users can also change the task title directly in the UI. Additionally, the app remembers tasks locally, guaranteeing that users' tasks are saved even when they refresh the page or return to the app later.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/).

## Project Setup
### Clone the project
```sh
git clone https://github.com/Kairu009/Task-Management.git
```

### Open file directory
```sh
cd Task-Management
```

### Install project dependencies
```sh
npm install
```

### Compile and Hot-Reload for Development
```sh
npm run dev
```

## Screenshot

By default, the user is prompted to the login screen unless they have already logged in, and it is saved to the browser's local storage unless the user closes the browser.

![1](https://github.com/Kairu009/Task-Management/assets/139950310/03d1c702-eb9e-4ec7-9fcb-609e3d170e88)

![2](https://github.com/Kairu009/Task-Management/assets/139950310/6607ad68-2464-43d6-8806-a0b4bcdc8e0a)

By default, Task View displays "No tasks available" and both counters are set to 0 until the user inserts a task, at which point the counter increases based on the total task and completed tasks.

![3](https://github.com/Kairu009/Task-Management/assets/139950310/7a71ba7e-8b1b-472d-ae50-9b9d43bf73d7)

![6](https://github.com/Kairu009/Task-Management/assets/139950310/5e9ef16d-a113-43bc-83a9-6dae07fd17e5)

Here is a view of the local storage, where you can see the user and password, as well as the task array where the task is stored, which contains the title or name of the task and whether or not the task has been completed.

![7](https://github.com/Kairu009/Task-Management/assets/139950310/cda3b7da-5bb5-442c-980f-cc28e2cc1f0d)

![8](https://github.com/Kairu009/Task-Management/assets/139950310/0e860e82-8e0c-431c-94a8-6c08b79f1d9f)
