# github_blocklist

github_blocklist provides a simple tool to manage your github blocks &
distributed blocklist.

Right now it relies on `gh` for auth and posting to the API.

## Usage

Start by storing your current blocks in a text file:

```
$ gh api /user/blocks | jq .[].login -r | sort -f > personal_list.txt
```

and edit that file as needed, removing any users you'd like to unban,
adding users, etc.

Then, periodically, pull this source to update the lists and then
rerun:

```
$ git pull
$ ./bin/github_block lists/* personal_list.txt
```

If you want to be selective about which blocks you apply, run it like so:

```
$ ./bin/github_block lists/{ai,abusers,...} personal_list.txt
```
