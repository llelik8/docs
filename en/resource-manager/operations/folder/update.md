# Update a folder

The management console only allows you to change the name of a folder. To change its description, use the CLI or API.

---

**[!TAB Management console]**

1. In the management console, click ![image](../../../_assets/ugly-sandwich.svg) and go to **Access management**.
2. Click ![image](../../../_assets/dots.svg) next to the folder and select **Rename**.
3. Enter a new name for the folder.
4. Click **Rename**.

**[!TAB CLI]**

1. See the description of the update folder command:

    ```
    $ yc resource-manager folder update --help
    ```

2. If you know the folder ID or name, proceed to the next step. If not, use one of these methods to get them:

    * Get a list of folders:

        ```
        $ yc resource-manager folder list
        +----------------------+--------------------+--------+--------+-------------+
        |          ID          |        NAME        | LABELS | STATUS | DESCRIPTION |
        +----------------------+--------------------+--------+--------+-------------+
        | b1gppulhhm2aaufq9eug | yet-another-folder |        | ACTIVE |             |
        | b1gvmob03goohplct641 | default            |        | ACTIVE |             |
        +----------------------+--------------------+--------+--------+-------------+
        ```

    * If you know the ID of the resource that belongs to the required folder, you can get the folder ID from the information about that resource:

        ```
        $ yc <SERVICE-NAME> <RESOURCE> get <RESOURCE-ID>
        ```

        where:
        * `<SERVICE-NAME>` is the name of the service, such as `compute`.
        * `<RESOURCE>` is the category of the resource, such as `instance`.
        * `<RESOURCE-ID>` is the resource identifier.

        For example, the `fhmp74bfis2aim728p2a` VM belongs to the `b1gpvjd9ir42nsng55ck` folder:

        ```
        $ yc compute instance get fhmp74bfis2ais728p2a
        id: fhmp74bfis2ais728p2a
        folder_id: b1gpvjd9ia42nsng55ck
        ...
        ```

3. Change the folder parameters, such as name and description. You can specify the folder to update by its name or ID.

    ```
    $ yc resource-manager folder update default \
        --new-name myfolder \
        --description "this is my default-folder"
    ```

    The command will rename the `default` folder to `myfolder` and update its description.

    [!INCLUDE [name-format](../../../_includes/name-format.md)]

**[!TAB API]**

To update the folder, use the [update](../../api-ref/Folder/update.md) method for the [Folder](../../api-ref/Folder/index.md) resource.

---

