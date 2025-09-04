import socket

def scan_port(host, port):
    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.settimeout(1)  # Set a timeout for connection attempts
        result = s.connect_ex((host, port))
        if result == 0:
            print(f"Port {port} is open on {host}")
        s.close()
    except socket.error as e:
        print(f"Error connecting to {host}:{port} - {e}")

# Example usage:
target_host = "example.com"
for p in range(1, 1025):  # Scan common ports
    scan_port(target_host, p)
