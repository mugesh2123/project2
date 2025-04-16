# project2
# Automated Port Scanning on AWS EC2 using Bash Scripting and Nmap

A simple tool that uses Bash and Nmap on AWS EC2 to scan IPs or websites.It automatically finds open, closed, and filtered ports.Useful for basic cybersecurity testing

# technologies used
        1.aws cloud to run the EC2 server
        2.virtual box to run kali os 
        3.nmap for network scan to identify open,closed port in the server
        4.bash scripting to use automated task of network scan

# bash scripting for ports scan to identify the port open or closed

     read -p "Enter the IP address to scan: " ip
     sleep 3
     read -p "Enter the ports to scan (space separated): " ports
     sleep 3
     for port in $ports
     do
    echo " Scanning port $port on $ip....."
    
    result=$(nmap -p  $port $ip | grep "/tcp")
    if echo "$result" | grep -q  "open" 
    then
        echo " Port $port is OPEN on $ip"
    else
        echo " Port $port is CLOSED or FILTERED on $ip"
    fi

    echo "----------------------------------------------"
    sleep 3
done

# bash scripting for normal scan in the EC2 server
      read -p " Enter the ip or domain to scan "  target
      nmap  $target > result.txt
      echo " Scan has been completed and saved the report in result.txt"

      
