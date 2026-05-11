# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
Server Program (server.py) 
s = socket.socket()

s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")

conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()

    if not data:
        break

    print("Frames received:", data)

    ack = "ACK for " + data
    conn.send(ack.encode())

Client Program (client.py)
import socket

client = socket.socket()
client.connect(('localhost', 8000))

frames = ["Frame1", "Frame2", "Frame3", "Frame4"]
w = 2
i = 0

while i < len(frames):
    send_frames = frames[i:i+w]

    for frame in send_frames:
        print("Sending:", frame)
        client.send(frame.encode())

        ack = client.recv(1024).decode()
        print("Received:", ack)

    i += w

client.close()
conn.close()
Developed by Farzana M (212225040087)
## OUPUT

<img width="1910" height="1111" alt="Screenshot 2026-05-11 090816" src="https://github.com/user-attachments/assets/af3eb731-d0fe-4185-9466-1b9e6938e761" />

<img width="1919" height="1102" alt="Screenshot 2026-05-11 090832" src="https://github.com/user-attachments/assets/638e85f3-9482-48bc-a2b5-6f22b04b20fb" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
