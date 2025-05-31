import socket


    # Common ports to scan
    ports = [21, 22, 23, 25, 53, 80, 110, 443, 8080]

    print(f"\nScanning {target}...\n")
    for port in ports:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)  # Timeout for connection attempt

        result = sock.connect_ex((target, port))
        if result == 0:
            print(f"[+] Port {port} is open")
        else:
            print(f"[-] Port {port} is closed")
        sock.close()

if __name__ == "__main__":
    target = input("Enter the target IP address or hostname: ")
    scan_ports(target)
