# User Account Setup
This section covers basic account setup that will allow you to begin your journey with FlowWide Workbench!
(log_in_adm)=
## Log in as admin
First of all you need to log in as admin to [Keycloack](https://www.keycloak.org/)
To do it, you need to go to sub-url on your subinstance of workbench eg. <https://yourInstanceHere-gw.flowide.net/auth>.
For purpose of this documentation we will be using *f2c* instance so <https://f2c-gw.flowide.net/auth>

After opening the url you will be able to chose **Administration Console** as shown on the image below:

![Adminstration Console Selecetion Screen](./images/account_setup/admin_console_selection.png "Console Selection")

Next step is to log in as admin with **Your Provided Credentials**:

![Admin log in](./images/account_setup/admin_log_in.png "Admin Log In")

If everything went fine you should see a screen simmilar to this:

![Admin logged in](./images/account_setup/admin_logged_in.png "Admin Logged In")
(create_user)=
## Create new user

To create a new user you need to go to **your instance section**:

![Instance Change](./images/account_setup/instance_change.png "Instance Change")

Then select **Users** tab on a sidebar menu:

![Users Tab](./images/account_setup/users_tab.png "Users Tab")

Next select **Add User**
![Add User](./images/account_setup/add_user.png "Add User")

Next we are prepareing user's info:

![Create User](./images/account_setup/create_user.png "Create User")

1. Enter Username and user's email
2. If you are sure user's email is valid select that option, if You are not sure skipp it
3. Enter First and Last Name of the user
4. If you want to be able to access created account select that option
5. Here you can set up acctions user will be required to perform after first login - in our case selected option is *update password*
6. If you want to add your user to some group you can do it here.

Next we create user using **Create** button:

![Create](./images/account_setup/create_btn.png "Create")

(set_up_psswd)=
## Set up new user's password

To set up new user's password and allow him to log in, you need to go to **Credentials** tab in user details page and click on the **Set password** button.

![Set psswd](./images/account_setup/psswd.png "Set psswd")

Then you are able to enter new password for the user, and set the *Temporary* flag, which forces user to change the password on first log in. To confirm  setting up a new password click **Save**.

![Save](./images/account_setup/save.png "Save")

***Good job now you can set up permissions to your new user! Go to [Permissions](permissions) part of this manual to do it!***
