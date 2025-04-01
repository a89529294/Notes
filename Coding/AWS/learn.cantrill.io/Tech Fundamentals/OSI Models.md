## 7 Layer Model

1. **Layer 7: Application**
    - Direct interaction with end-user applications (e.g., HTTP, FTP, SMTP).
2. **Layer 6: Presentation**
    - Data translation, encryption/decryption, compression (e.g., SSL/TLS, JPEG).
3. **Layer 5: Session**
    - Manages communication sessions (establishing, maintaining, terminating).
    - Examples: NetBIOS, RPC.
4. **Layer 4: Transport**
    - Ensures end-to-end communication (reliability, flow control, error correction).
    - Examples: TCP (reliable), UDP (unreliable).
5. **Layer 3: Network**
    - Logical addressing and routing (e.g., IP, routers).
6. **Layer 2: Data Link**
    - Physical addressing (MAC), error detection (e.g., Ethernet, switches).
7. **Layer 1: Physical**
    - Raw bit transmission over hardware (e.g., cables, hubs, NICs).

### **Media vs. Host Layers:**

- **Media Layers (1–3):**
    - Focus on **how data moves** (physical transmission, framing, routing).
- **Host Layers (4–7):**
    - Focus on **data processing** (segmentation, session management, application logic).

### **Data Flow Explained:**

1. **Client (Sender) Side:**
    - **Top-Down (Layer 7 → Layer 1):**  
        The data starts at the **Application Layer (L7)** (e.g., a user sends an HTTP request) and moves down through each layer, getting "wrapped" with headers, trailers, and protocol-specific information at each step.
        - **Example:** An email (L7) → Encrypted (L6) → Session established (L5) → Split into TCP segments (L4) → Packets with IP addresses (L3) → Frames with MAC addresses (L2) → Raw bits sent over a cable (L1).
2. **Transmission Over the Network:**
    - The physical bits (L1) travel through cables, switches (L2), and routers (L3) to reach the server.
3. **Server (Receiver) Side:**
    - **Bottom-Up (Layer 1 → Layer 7):**  
        The server receives the raw bits (L1) and "unwraps" the data moving up each layer:
        - **Example:** Bits (L1) → Frames checked (L2) → IP routing (L3) → TCP reassembly (L4) → Session validation (L5) → Decryption (L6) → Delivered to the email server app (L7).    

### **Key Points:**

- **Encapsulation (Client):** Each layer adds its own header/trailer (e.g., L4 adds TCP ports, L3 adds IP addresses).
- **Decapsulation (Server):** Each layer removes its respective header/trailer and processes the payload.
- **Layer 4 (Transport) is critical:** It ensures data arrives intact (TCP) or fast (UDP), acting as the bridge between software (L5–7) and network (L1–3).