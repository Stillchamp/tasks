# tasks
# Create a new file: Use a text editor vim to create a new file name it multiplication.sh
using vim  multiplication.sh
# create a scripts file
<img width="1280" height="800" alt="Screen Shot 2025-08-31 at 8 26 40 AM" src="https://github.com/user-attachments/assets/9893ca5d-07fa-460b-987c-3dd7609f8873" />
#!/bin/bash

# A script to generate a multiplication table for a user-specified number.

## Function to validate if a string is a valid integer.
is_integer() {
    [[ "$1" =~ ^[0-9]+$ ]]
}

## Prompt the user to enter a number.
read -p "Enter a number to generate a multiplication table for: " num

## Input validation: check if the input is a valid positive integer.
if ! is_integer "$num" || [ "$num" -le 0 ]; then
    echo "Invalid input. Please enter a positive integer."
    exit 1
fi

## Prompt for the type of table: full or partial.
read -p "Do you want a full (1-10) or partial multiplication table? (f/p): " table_type

## Convert input to lowercase for case-insensitive comparison.
table_type=${table_type,,}

## Conditional logic: handle full vs. partial table choice.
if [ "$table_type" == "f" ]; then
    start=1
    end=10
elif [ "$table_type" == "p" ]; then
    ## Prompt for the start and end of the range for a partial table.
    read -p "Enter the start of the range: " start
    read -p "Enter the end of the range: " end

    ## Validate range inputs.
    if ! is_integer "$start" || ! is_integer "$end" || [ "$start" -le 0 ] || [ "$end" -le 0 ] || [ "$start" -gt "$end" ]; then
        echo "Invalid range. Displaying full table (1-10) instead."
        start=1
        end=10
    fi
else
    ## Default to a full table for invalid choices.
    echo "Invalid choice. Displaying full table (1-10)."
    start=1
    end=10
fi

echo ""
echo "Multiplication Table for $num:"
echo "------------------------------"

## Use a loop to generate and display the multiplication table.
for ((i=start; i<=end; i++)); do
    result=$((num * i))
    printf "%d x %d = %d\n" "$num" "$i" "$result"
done


# use of chom U+x 
# run the script file using ./multiplication.sh

# this are the results
<img width="1280" height="800" alt="Screen Shot 2025-08-31 at 8 28 58 AM" src="https://github.com/user-attachments/assets/b1b6c06b-c24c-4800-a91e-4efce0b51db3" />
<img width="1280" height="800" alt="Screen Shot 2025-08-31 at 8 29 02 AM" src="https://github.com/user-attachments/assets/44bb3ce2-d839-4d18-9e3b-9cd7f6e4a663" />
