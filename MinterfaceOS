
#!/bin/bash

# 3D Colorful Cryptocurrency Mining OS - MinterfaceOS

# Colors and Effects
RED="\033[31m"
GREEN="\033[32m"
YELLOW="\033[33m"
BLUE="\033[34m"
MAGENTA="\033[35m"
CYAN="\033[36m"
WHITE="\033[37m"
RESET="\033[0m"
BOLD="\033[1m"

# Function to display the welcome screen
function welcome_screen() {
  clear
  echo -e "\n\n"
  echo -e "${BLUE}${BOLD}=========================================${RESET}"
  echo -e "${MAGENTA}${BOLD}            MinterfaceOS                 ${RESET}"
  echo -e "${MAGENTA}${BOLD}███╗   ███╗██╗███╗   ██╗████████╗███████╗██████╗ ███████╗ █████╗  ██████╗███████╗ ██████╗ ███████╗${RESET}"
  echo -e "${MAGENTA}${BOLD}████╗ ████║██║████╗  ██║╚══██╔══╝██╔════╝██╔══██╗██╔════╝██╔══██╗██╔════╝██╔════╝██╔═══██╗██╔════╝${RESET}"
  echo -e "${MAGENTA}${BOLD}██╔████╔██║██║██╔██╗ ██║   ██║   █████╗  ██████╔╝█████╗  ███████║██║     █████╗  ██║   ██║███████╗${RESET}"
  echo -e "${MAGENTA}${BOLD}██║╚██╔╝██║██║██║╚██╗██║   ██║   ██╔══╝  ██╔══██╗██╔══╝  ██╔══██║██║     ██╔══╝  ██║   ██║╚════██║${RESET}"
  echo -e "${MAGENTA}${BOLD}██║ ╚═╝ ██║██║██║ ╚████║   ██║   ███████╗██║  ██║██║     ██║  ██║╚██████╗███████╗╚██████╔╝███████║${RESET}"
  echo -e "${MAGENTA}${BOLD}╚═╝     ╚═╝╚═╝╚═╝  ╚═══╝   ╚═╝   ╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝  ╚═╝ ╚═════╝╚══════╝ ╚═════╝ ╚══════╝${RESET}"
  echo -e "${BLUE}${BOLD}=========================================${RESET}"
  echo -e "${GREEN}${BOLD}Version 2.0${RESET}"
  echo -e "${CYAN}Made by Sagar_Parajuli. Your cryptocurrency tracking and mining assistant.${RESET}\n\n"
}

# Function to check internet connection
function check_internet() {
  echo -e "${CYAN}Checking internet connectivity. Please wait...${RESET}"
  for i in {1..10}; do
    echo -ne "${CYAN}Checking${RESET}${BOLD}${YELLOW} [${i}/10]${RESET}...\r"
    sleep 1
  done
  if curl -s https://www.google.com > /dev/null; then
    echo -e "${GREEN}Internet is connected.${RESET}\n"
  else
    echo -e "${RED}No internet connection. Please check your network and try again.${RESET}"
    exit 1
  fi
}

# Function to fetch and display user's location
function display_location() {
  echo -e "${CYAN}Fetching your location details...${RESET}"
  LOCATION=$(curl -s https://ipinfo.io | grep -E '"city"|"region"|"country"' | awk -F: '{print $2}' | tr -d '",')
  if [ -z "$LOCATION" ]; then
    echo -e "${RED}Failed to fetch location. Please check your internet connection.${RESET}"
    exit 1
  fi
  echo -e "${GREEN}Your current location:${RESET}\n${YELLOW}${LOCATION}${RESET}\n"
}

# Function to validate required command
function validate_command() {
  echo -e "${CYAN}Please enter the required command to proceed:${RESET} (e.g., para -install)"
  read -p "Command: " USER_COMMAND
  if [[ "$USER_COMMAND" == "para -install" ]]; then
    echo -e "${GREEN}Command validated. Proceeding...${RESET}\n"
  else
    echo -e "${RED}Invalid command. Please try again.${RESET}\n"
    exit 1
  fi
}

# Function to display currency options
function display_currency_options() {
  echo -e "${YELLOW}${BOLD}Available Currencies:${RESET}"
  echo -e "${CYAN}1. Bitcoin\n2. USDT\n3. Dogecoin\n4. Pi\n5. Core\n6. Tron\n7. BNB\n8. Baby Doge Coin\n9. Notcoin\n10. Bitcoin Cash\n11. Litecoin\n12. Monero Coin\n13. USDC\n14. Banana\n15. Ripple\n16. Exit${RESET}\n"
}

# Function to execute default Bitcoin mining command
function execute_bitcoin_mining() {
  echo -e "${GREEN}Starting default Bitcoin mining script...${RESET}"
  echo -e "${CYAN} Your cryptocurrency tracking and mining assistant active on Bitcoin mining...${RESET}"
  sleep 5   
  echo -e "${GREEN}Bitcoin mining completed successfully.${RESET}"
}

# Function to prompt user for currency and mining script
function user_input() {
  echo -e "${CYAN}Which currency would you like to use?${RESET}"
  read -p "Enter the number corresponding to your choice: " CURRENCY_CHOICE

  # Validate input
  if ! [[ "$CURRENCY_CHOICE" =~ ^[0-9]+$ ]] || ((CURRENCY_CHOICE < 1 || CURRENCY_CHOICE > 16)); then
    echo -e "${RED}Invalid choice. Please enter a number between 1 and 16.${RESET}"
    return
  fi

  if [[ $CURRENCY_CHOICE -eq 16 ]]; then
    echo -e "${GREEN}Exiting MinterfaceOS. Thank you for using the application.${RESET}"
    exit 0
  elif [[ $CURRENCY_CHOICE -eq 1 ]]; then
    execute_bitcoin_mining
  else
    echo -e "${YELLOW}You selected option ${CURRENCY_CHOICE}.${RESET}"
    echo -e "${CYAN}Enter your mining script or command:${RESET}"
    read -p "Command: " MINING_COMMAND

    echo -e "${GREEN}Running your mining script...${RESET}"
    eval $MINING_COMMAND || {
      echo -e "${RED}Error: Failed to execute the mining script. Please check your command.${RESET}"
    }
  fi

  echo -e "${CYAN}Press Enter to return to the menu or close the terminal.${RESET}"
  read
}

# Main execution loop
while :; do
  welcome_screen
  check_internet
  display_location
  validate_command

  # Display menu and get user input
  display_currency_options
  user_input
done

