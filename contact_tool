#!/bin/bash


while getopts ":n :h" option; do
	case  "${option}" in
		n)	
printf "Select from the following options:\n 1) Add a Contact\n 2) Remove a Contact\n 3) Display Contact Info\n"
read -p "Selection: " Selection1
  case "$Selection1" in
    1) 
      if [ ! -d "./contacts" ]
      then  
	  mkdir contacts
      fi
      echo "You selected Add a Contact"
      read -p "Please Enter their Address: " address 
      read -p "Please Enter their Email: " email
      read -p "Please Enter their Name: " name
      read -p "Please Enter their Phone: " phone
      FILE_PATH=./contacts/$name
      if [ -e "$FILE_PATH" ]
      then
	      read -p "This contact already exists would you like to overwrite it? :" y_n
	      case "$y_n" in
		      y)
			      echo "Overwriting..." 
      	      		      printf "Address: $address \n Email: $email \n Name: $name \n Phone: $phone \n" > $FILE_PATH
	              ;;
      		      n)
			 echo "no changes were made"
                         exit 0
	     	      ;;
	              esac
      else    
      	      printf "Address: $address \n Email: $email \n Name: $name \n Phone: $phone \n" > $FILE_PATH
      fi
      ;;
    
    2)
      echo "You selected to delete a Contact"
      read -p "Please enter the name you would like to delete: " name
      rm "contacts/$name"
      ;;
    3)
      echo "Contact info:"
      read -p "Please Enter the name of the contact you would like to view: " name
      ContactFile="./contacts/$name"  
      if [ ! -e "$ContactFile" ]
      then
	echo "User does not exist"
      else	
      	while read -r line_item; do
	  echo $line_item
      	done < "$ContactFile"
      fi
      ;;
    *)
      echo "Invalid selection"
      ;;
  esac
  ;;
  h)
    printf "The contacts are identified by name only. \n"
    echo "Case 1: Create a contact, adds the address,email,name and phone number to a file  named after the contact"
    echo "Case 2: Deletes the contact file for a contact once the name is entered."
    echo "Case 3: Prints the information of a contact once you enter the name"
  ;;
  *) 	  
    echo "Arguments required -n = [Normal start], -h = [Help]"
  ;;
esac
done

if [[ $# -lt 1 ]]; then
   echo "Arguments required -n = [Normal start], -h = [Help]"
fi
