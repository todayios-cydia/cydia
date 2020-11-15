# [TSCydia](https://todayios-cydia.github.io/cydia/)
A Cydia repository  `https://todayios-cydia.github.io/cydia/`.

## Adding packages first package to your repo

#### 1. Adding a simple depiction page

Go to the depictions folder and duplicate the folder `com.todayios-cydia.woodpecker`.
Rename the duplicate with the same name as your package name.
There are 2 files inside the folder - `info.xml` and `changelog.xml`.
Update the 2 files with information regading your package.
The tags are pretty much self-explanatory.

`info.xml`.
```xml
<package>
    <id>com.todayios-cydia.woodpecker</id>
    <name>WoodPecker</name>
    <version>1.2.9/version>
    <compatibility>
        <firmware>
            <miniOS>9.0</miniOS>
            <maxiOS>14.0</maxiOS>
            <otherVersions>unsupported</otherVersions>
            <!--
            for otherVersions, you can put either unsupported or unconfirmed
            -->
        </firmware>
    </compatibility>
    <dependencies></dependencies>
    <descriptionlist>
        <description>This is an woodpecker package.</description>
    </descriptionlist>
    <screenshots></screenshots>
    <changelog>
        <change>Initial release</change>
    </changelog>
    <links></links>
</package>
```

`changelog.xml`.
```xml
<changelog>
    <changes>
        <version>1.2.9</version>
        <change>Initial release</change>
    </changes>
</changelog>
```


#### 2. Link the depiction page your tweak's `control` file

For the depictions to appear on Cydia, you will need to add the depictions url at the end of your package's `control` file before compiling it.
The control file should look like this:

```text
Package: com.todayios-cydia.woodpecker
Name: WoodPecker
Section: Tweaks
Depends: firmware (>12.0)
Description: This is a sample package. Firmware should be greater than 12.0
Depiction: https://todayios-cydia.github.io/cydia/depictions/?p=[idhere]
```

Replace `[idhere]` with your actual package name.

```text
Depiction: https://todayios-cydia.github.io/cydia/depictions/?p=com.todayios-cydia.woodpecker
```

#### 3. Rebuilding the `Packages` file

With your updated `control` file, build your tweak.
Store the resulting `.deb.` file into the `/debs/` folder of your repo.
Build your `Packages` file and compress with `bzip2`.

```sh
cd repo
dpkg-scanpackages -m ./debs > Packages
bzip2 Packages
```

Also you can use the `update.sh` shell

_Windows users, see [dpkg-scanpackages-py](https://github.com/supermamon/dpkg-scanpackages-py) or [scanpkg](https://github.com/mstg/scanpkg)._