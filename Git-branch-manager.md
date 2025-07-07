\#!/bin/bash



echo "🌿 Git Branch Manager"



while true; do

&nbsp; echo ""

&nbsp; echo "Choose an option:"

&nbsp; echo "1. List all branches (local \& remote)"

&nbsp; echo "2. Create a new branch"

&nbsp; echo "3. Switch to a branch"

&nbsp; echo "4. Delete a branch"

&nbsp; echo "5. Show merged/unmerged branches"

&nbsp; echo "0. Exit"



&nbsp; read -p "Your choice: " choice



&nbsp; case $choice in

&nbsp;   1)

&nbsp;     echo "Local branches:"

&nbsp;     git branch

&nbsp;     echo ""

&nbsp;     echo "Remote branches:"

&nbsp;     git branch -r

&nbsp;     ;;

&nbsp;   2)

&nbsp;     read -p "Enter new branch name: " new\_branch

&nbsp;     git checkout -b "$new\_branch"

&nbsp;     echo "Switched to new branch: $new\_branch"

&nbsp;     ;;

&nbsp;   3)

&nbsp;     read -p "Enter branch name to switch to: " branch\_to\_switch

&nbsp;     git checkout "$branch\_to\_switch"

&nbsp;     echo "Switched to branch: $branch\_to\_switch"

&nbsp;     ;;

&nbsp;   4)

&nbsp;     read -p "Enter branch name to delete: " branch\_to\_delete

&nbsp;     read -p "Are you sure? This will delete the branch locally (y/n): " confirm

&nbsp;     if \[ "$confirm" == "y" ]; then

&nbsp;       git branch -d "$branch\_to\_delete"

&nbsp;       echo "Deleted branch: $branch\_to\_delete"

&nbsp;     else

&nbsp;       echo "Cancelled delete."

&nbsp;     fi

&nbsp;     ;;

&nbsp;   5)

&nbsp;     echo "Merged branches:"

&nbsp;     git branch --merged

&nbsp;     echo ""

&nbsp;     echo "Unmerged branches:"

&nbsp;     git branch --no-merged

&nbsp;     ;;

&nbsp;   0)

&nbsp;     echo "Exiting Git Branch Manager."

&nbsp;     break

&nbsp;     ;;

&nbsp;   \*)

&nbsp;     echo "Invalid option. Please try again."

&nbsp;     ;;

&nbsp; esac

done

