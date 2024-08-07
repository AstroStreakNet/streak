
# Streak

Streak is a utility tool for managing and interacting with the AstroStreak
platform. It is designed to be POSIX compliant, ensuring compatibility across
different UNIX based operating systems (GNU+Linux / macos).

## Usage

Streak provides various commands for managing your AstroStreak account and
interacting with the image database.

### Available Commands

- **account:** Manage your AstroStreak account status
- **browse:** Browse images based on specified criteria
- **help:** Get help about any command 

### Example Usage 

Upload images from the *"captures"* directory within ~/Pictures to the database
with public visibility but without granting AI training permissions.
```sh
$ streak --no-ai ~/Pictures/captures/*
$ streak -N ~/Pictures/captures/*
```

Upload all FITS files captured today located in the *"saves"* directory within
the ~/Pictures with default flags.
```sh
$ streak $(find ~/Pictures/saves/ -iname "*.fits" -type f -mtime -1)
$ find ~/Pictures/saves/ -iname "*.fits" -type f -mtime -1 | streak)
```

Count the number of images containing both the sun and the moon but not any
asteroids.
```sh
$ streak browse --all --contains "sun moon" --not-contains "astroid" | wc -l
$ streak browse -A -c "sun moon" -C "astroid" | wc -l
```

Download all images uploaded on February 26, 2024, permitted for AI training,
and save them in a directory named *"saved"* within the ~/Pictures.
```sh
$ streak browse --all --trainable --date "26-02-2024" --save ~/Pictures/saved
$ streak browse -A -t -d "26-02-2024" -s ~/Pictures/saved
```

## Project Origin
Streak was developed as a final year project for the Software Engineering
Honours program at Swinburne University of Technology.

