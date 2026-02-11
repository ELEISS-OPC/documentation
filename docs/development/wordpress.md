# Wordpress

We use Wordpress to host the [company landing page](https://infinetsolutionsph.com/).

## Developing locally

Developing locally is great and efficient way of building websites, but due to the nature of Wordpress, remote collaboration capabilities is limited.

### Docker Compose

We mainly use the [Docker Engine](https://docs.docker.com/engine/install) with [Docker Compose](https://docs.docker.com/compose/install/) for local development. The following `docker-compose.yml` file uses [Wordpress](https://hub.docker.com/_/wordpress) and [MySQL](https://hub.docker.com/_/mysql) docker images.

```yaml title="docker-compose.yml"
services:
  wordpress:
    image: wordpress
    restart: always
    ports:
      - 8081:80 #  Access Wordpress at http://localhost:8081.
        #  Change 8081 to a different port if needed.
    environment:
      WORDPRESS_DB_HOST: db # Change these credentials for security purposes
      WORDPRESS_DB_USER: exampleuser
      WORDPRESS_DB_PASSWORD: examplepass
      WORDPRESS_DB_NAME: exampledb
    volumes:
      - wordpress:/var/www/html

  db:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_DATABASE: exampledb # Change these credentials for security purposes
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
      MYSQL_RANDOM_ROOT_PASSWORD: "1"
    volumes:
      - db:/var/lib/mysql

volumes:
  wordpress:
  db:
```

!!! example "Usage Example"

    ```bash title="Command Line"
    docker compose up -d
    ```

    Make sure that the `docker-compose.yml` file is in the same working directory when composing up.
    Composing up builds and runs the containers. Once finished building and everything is healthy, Wordpress should be accessible at `http://localhost:8081`

## User Interface

We use the SaaS company theme as a base theme and extend and edit the theme from there. An in-depth styling and theming documentation is found [here](../branding/index.md).

### Lucide

We use [Lucide](https://lucide.dev/) for UI icons.

The following CSS is our `Additional CSS`.

```css
/* Custom Button Styling */
.wp-block-button__link {
  color: white;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5em;
}

/* Base Lucide Style */
.lucide {
  width: 1.2em;
  height: 1.2em;
  background-color: currentColor;
}
```

#### Adding a new icon

We can add a new icon to accompany buttons or to help important text standout more.
The following is a generic CSS icon class using the data URL of a Lucide icon.

```css
.icon-generic {
  mask: url("data:image/svg+xml;base64,...") no-repeat center;
  mask-size: contain;
}
```

Simply replace the `mask: url("...")` value with the data URL of your chosen icon then add this class to `Additional CSS`.
Then use both the `lucide` and `.icon-generic` class in an empty `div`'s class attribute.

!!! example "Demonstration"

    As a demonstration example, let's try adding this [heart icon](https://lucide.dev/icons/heart) to our website.

    === "Step 1-2"

        1) Navigate to the heart icon page and click the dropdown menu for copy options.

        2) Click `Copy Data URL`.

        ![Steps 1 to 2](../images/wordpress/new-lucide-icon-tutorial/step1-2.png)

    === "Step 3"

        3) Head over to the `Site Editor` page.

        ![Step 3](../images/wordpress/new-lucide-icon-tutorial/step3.png)

    === "Step 4-6"

        4) At the `Design` page, head over to `Styles`

        5) Click the dropdown options

        6) Click `Additional CSS`

        ![Steps 4 to 6](../images/wordpress/new-lucide-icon-tutorial/step4-6.png)

    === "Step 7"

        7) Prepare the CSS class and replace the `mask: url("...")` value with the data URL that you just copied. We appropriately name the class `.icon-heart`.

        ```css
        .icon-heart {
          mask: url("data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0IiBmaWxsPSJub25lIiBzdHJva2U9ImN1cnJlbnRDb2xvciIgc3Ryb2tlLXdpZHRoPSIyIiBzdHJva2UtbGluZWNhcD0icm91bmQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIGNsYXNzPSJsdWNpZGUgbHVjaWRlLWhlYXJ0LWljb24gbHVjaWRlLWhlYXJ0Ij48cGF0aCBkPSJNMiA5LjVhNS41IDUuNSAwIDAgMSA5LjU5MS0zLjY3Ni41Ni41NiAwIDAgMCAuODE4IDBBNS40OSA1LjQ5IDAgMCAxIDIyIDkuNWMwIDIuMjktMS41IDQtMyA1LjVsLTUuNDkyIDUuMzEzYTIgMiAwIDAgMS0zIC4wMTlMNSAxNWMtMS41LTEuNS0zLTMuMi0zLTUuNSIvPjwvc3ZnPg==")
            no-repeat center;
          mask-size: contain;
        }
        ```

        !!! tip

            Prepare the CSS class with your favorite text editor as the ones inside Wordpress is quite limited.


    === "Step 8"

        8) Copy and paste the `.icon-heart` CSS class into `Additional CSS`. Now we are ready to use this icon.

        ![Step 8](../images/wordpress/new-lucide-icon-tutorial/step8.png)


    === "Step 9-11"

        9) Pick your chosen block to insert your icon. We choose this `View Plans` button.

        10) Click the dropdown options

        11) Click `Edit as HTML`

        ![Steps 9 to 11](../images/wordpress/new-lucide-icon-tutorial/step9-11.png)

        !!! tip

            You can also alternatively use this with the `HTML` block.

    === "Step 12-13"

        12) Insert an empty `div` element and add class attributes `lucide` and `icon-heart`.

        13) Click `Edit visually` to see the results.

        ![Steps 12 to 13](../images/wordpress/new-lucide-icon-tutorial/step12-13.png)

        Done!

        ![Resulting design](../images/wordpress/new-lucide-icon-tutorial/result.png)

## Backups & Migrations

We use the [All-in-One WP Migration](https://github.com/d0n601/All-In-One-WP-Migration-With-Import) plugin to backup and migrate our Wordpress website.

### Installing the Plugin

To use the plugin, we must first [download the plugin](https://codeload.github.com/d0n601/All-In-One-WP-Migration-With-Import/zip/refs/heads/master) and then proceed with the following tutorial to install it.

=== "Step 1-2"

    1) Navigate to the `Plugins` page at the Wordpress dashboard.

    2) Click `Add Plugin`.

    ![Steps 1 to 2](../images/wordpress/install-plugin-tutorial/step1-2.png)

=== "Step 3-4"

    3) Click `Upload Plugin`.

    4) Upload the file `All-In-One-WP-Migration-With-Import-master.zip`.

    ![Steps 3 to 4](../images/wordpress/install-plugin-tutorial/step3-4.png)

=== "Step 5"

    5) Click `Install Now`

    ![Step 5](../images/wordpress/install-plugin-tutorial/step5.png)

=== "Step 6"

    6) Click `Activate Plugin`

    ![Step 6](../images/wordpress/install-plugin-tutorial/step6.png)

    Done!

### Exporting a backup

Performing backups regularly is essential to prevent minimal data loss whenever our hosting service fails and destroys our data or a irreversible destructive update to the website corrupts the data. The following tutorial demonstrates how to export a backup.

=== "Step 1-4"

    1) Navigate to the `All-in-One WP Migration` plugin page at the Wordpress dashboard.

    2) Navigate to `Export`.

    3) Click `EXPORT TO`.

    4) Click `FILE`.

    ![Steps 1 to 2](../images/wordpress/export-backups-tutorial/step1-4.png)

=== "Step 5"

    6) Click `DOWNLOAD <SITE DOMAIN>`. The site domain is at what domain name the Wordpress website uses.

    ![Step 5](../images/wordpress/export-backups-tutorial/step5.png)

    Done!

### Importing a backup

Importing a backup is used for restoring Wordpress from a backup file.

=== "Step 1-4"

    1) Navigate to the `All-in-One WP Migration` plugin page at the Wordpress dashboard.

    2) Navigate to `Import`.

    3) Click `IMPORT FROM`.

    4) Click `FILE` and select the backup file, it should be a `.wpress` file.

    ![Steps 1 to 4](../images/wordpress/import-backups-tutorial/step1-4.png)

=== "Step 5"

    !!! warning

        Make sure the data you are replacing right now is backed up otherwise proceed if it doesn't need to be backed up. Read the [relevant documentation](#exporting-a-backup) to backup your data.

    5) Click `PROCEED >`.

    ![Step 5](../images/wordpress/import-backups-tutorial/step5.png)

=== "Step 6-7"

    6) A popup will appear and click `Permalink Settings`.

    7) Navigate to the new tab that just opened.

    ![Step 6](../images/wordpress/import-backups-tutorial/step6-7.png)

=== "Step 8"

    8) Scroll to the bottom and click `Save Changes` twice.

    ![Step 7](../images/wordpress/import-backups-tutorial/step8.png)

    Done!

### Migrating Wordpress

To migrate a Wordpress instance, simply export a backup file of the source Wordpress instance, then import that backup file into the target Wordpress instance. Read the relevant documentation for [exporting](#exporting-a-backup) and [importing](#importing-a-backup) backups to learn more.
