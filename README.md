# 🎛️ LoginAppCSharp — UserLoginSystem (WinForms Demo)

[![Repo Size](https://img.shields.io/github/repo-size/Achintha-999/LoginAppCSharp)](https://github.com/Achintha-999/LoginAppCSharp)
[![Made with C#](https://img.shields.io/badge/Made%20with-C%23-239120?logo=csharp)](https://docs.microsoft.com/dotnet/csharp/)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20WinForms-blue?logo=windows)](#)
[![Target](https://img.shields.io/badge/Target-.NET%20Framework%204.7.2-lightgrey)](#)
[![License](https://img.shields.io/github/license/Achintha-999/LoginAppCSharp)](https://github.com/Achintha-999/LoginAppCSharp/blob/main/LICENSE)

--------------------------------------------------------------------------------
A small, focused Windows Forms (WinForms) login demo written in C#. This project demonstrates a very simple login UI and logic (no database, no external services) and is intended for learning or quick demos.

Quick visual:
- 🖥️ WinForms desktop app
- 🔐 Demo authentication (hard-coded credentials)
- ❗ No database required — credentials are checked in code
- ⚠️ Not production-ready — insecure defaults exist on purpose for demonstration

--------------------------------------------------------------------------------
Table of contents
- About
- Features
- Requirements
- How it works (quick)
- Files & structure
- Build & Run (Windows / Visual Studio)
- Customize (change credentials / messages)
- Security notes
- Troubleshooting
- Contributing & License
- Contact

About
-----
A minimal login application implemented as a WinForms project named "UserLoginSystem". It shows a login form, checks credentials, and opens a HomePage form on success. The project is intentionally small and readable for people learning WinForms.

Features
--------
- Simple username & password login screen
- Demo authentication using in-code credential check (no DB, no files)
- Small, easy-to-read codebase suitable for learning WinForms basics
- Example of navigating from a login form to a main/home form

Requirements
------------
- OS: Windows (WinForms desktop application)
- Visual Studio 2019/2022 (recommended) or any IDE that supports .NET Framework WinForms
- .NET Framework 4.7.2 (target specified in project)
- No database or external services required

How it works (quick)
--------------------
1. The application entry is in Program.cs — Application.Run(new Form1()).
2. Form1 contains the login UI (username and password textboxes) and a Button click handler.
3. When the user clicks the login button, the code checks the entered values against the hard-coded demo credentials.
   - If match -> instantiate HomePage, Show() it and Hide() the login form.
   - If not match -> show a MessageBox with "Invalid username or password".
4. HomePage is a blank (or simple) form that acts as the post-login screen.

Key code snippet (login check)
```csharp
// in UserLoginSystem/Form1.cs (button click handler)
if (tb_username.Text == "admin" && tb_password.Text == "123")
{
    HomePage homePage = new HomePage();
    homePage.Show();
    this.Hide();
}
else
{
    MessageBox.Show("Invalid username or password. Please try again.", "Login Failed", MessageBoxButtons.OK, MessageBoxIcon.Error);
}
```

Files & project structure
-------------------------
- UserLoginSystem/
  - Form1.cs            — Login form + login logic
  - HomePage.cs         — Simple form shown after successful login
  - Program.cs          — Application entry point
  - Properties/AssemblyInfo.cs
  - obj/                — build artefacts (ignore)
- README.md
- LICENSE (if present)

Build & Run (Windows / Visual Studio)
------------------------------------
1. Clone the repository:
   git clone https://github.com/Achintha-999/LoginAppCSharp.git
2. Open Visual Studio.
3. Open the project:
   - Either open the solution if present, or open the UserLoginSystem/UserLoginSystem.csproj file.
4. Build the project (Build → Build Solution).
5. Run the project (Debug → Start Debugging or press F5).
6. Login screen appears. Demo credentials (for quick test):
   - Username: admin
   - Password: 123

Alternative (command-line build):
- Use MSBuild (available with Visual Studio tools):
  msbuild UserLoginSystem\UserLoginSystem.csproj /p:Configuration=Debug
- Run the generated executable from bin\Debug\ (e.g., UserLoginSystem.exe).

Customize (change credentials / behavior)
-----------------------------------------
- To change the demo credentials, open UserLoginSystem/Form1.cs and edit the if-check in the button click handler.
- To replace the in-code check with a more realistic approach (configuration file or secure store), modify the authentication logic in Form1.cs or move it to a separate class for clarity.

Security notes (IMPORTANT)
--------------------------
- This project uses hard-coded credentials for demonstration. This is insecure and should never be used in production.
- No password hashing or storage is implemented here.
- If you want to use this as a starting point for a real app:
  - Replace hard-coded credentials with a proper authentication provider.
  - Use secure storage and hashed passwords (bcrypt / PBKDF2 / Argon2).
  - Add input validation and consider account lockout/brute-force mitigation.
- For learning and demos, this code is intentionally simple.

Troubleshooting
---------------
- If Visual Studio reports missing .NET Framework target, install Developer Pack for .NET Framework 4.7.2.
- If you see no UI on launch, ensure Program.cs calls Application.Run(new Form1()).
- If the app immediately closes, run it from Visual Studio with the debugger attached to view exceptions.

Contributing
------------
This is a small demo. Contributions that improve clarity, add comments, or make the demo safer (while keeping a demo mode) are welcome:
1. Fork the repo
2. Create a branch (feature/your-change)
3. Submit a PR with explanation of your changes

License
-------
Check the LICENSE file in the repository. If present, it is applied to this codebase.

Acknowledgements
----------------
Made for learning WinForms and quick demos. Thanks to the C# and .NET communities.

Contact
-------
Maintainer: Achintha-999 (GitHub)

--------------------------------------------------------------------------------
Have fun exploring WinForms — if you'd like, I can also:
- Replace the hard-coded check with a simple credential file (JSON) while keeping "no DB",
- Or add a toggle to the UI to enable/disable demo-mode credentials.
