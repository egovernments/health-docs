# Peer To Peer Transfer

## Overview

This feature enables peer-to-peer (P2P) data exchange between devices **without internet**, leveraging Google Nearby Connections API and Wi-Fi Direct, Bluetooth, or Wi-Fi Hotspot. Data is securely transmitted using compression, AES encryption, and Base64 encoding.

***

## Architecture Components

### Device Communication Layer

**Nearby Connections API (Google)**

* **Discovery/Connection**:\
  Uses BLE for discovery, Wi-Fi Direct/Hotspot for transfer, and automatically selects the best medium.
* **Roles**:
  * **Advertiser**: Device making itself available
  * **Discoverer**: Device searching for peers

**Supported Topologies**

* **P2P\_CLUSTER**: Mesh, several devices, low bandwidth, suitable for multiplayer/gaming.
* **P2P\_STAR**: One hub, others connect to it, ideal for content sharing.
* **P2P\_POINT\_TO\_POINT**: Direct 1-to-1, highest speed, best for large files.
* **Wi\_Fi\_P2P**: Wi-Fi Direct, long-range, for games or large files.

**Connection Selection Logic**

* On connection attempt, use:
  * BLE for initial discovery
  * Wi-Fi Direct/Hotspot for large/high-speed transfers
  * Fallback to Bluetooth if Wi-Fi is not available

***

### Secure Payload: Compression & Encryption

#### **Compression (zlib/GZipEncoder)**

* **Input**: JSON-encoded Dart Map
* **Process**:
  * Convert JSON string to UTF-8 bytes
  * Compress using GZipEncoder
* **Output**: Compressed byte array

***

#### **Encryption (AES-CBC via encrypt package)**

* **Key Generation**: 32-byte random key (AES-256)
* **IV Generation**: 16-byte random IV
* **Algorithm**: AES in CBC mode
* **Process**:
  * Encrypt compressed bytes with AES-CBC using key & IV
* **Security Notes**:
  * Unique IV per encryption for semantic security
  * Key+IV must be securely stored or sent with the payload

***

#### **Base64 Encoding**

* **Purpose**: Convert binary (key, IV, encrypted data) to URL/text/QR-compatible string
* **Process**:
  * Encode each part (key, IV, data) as Base64 URL-safe
  *   Wrap into a JSON:

      ```json
      {
        "key": "<Base64-encoded AES key>",
        "iv": "<Base64-encoded IV>",
        "data": "<Base64-encoded encrypted data>"
      }
      ```
  * Encode the full JSON as a final Base64 URL-safe string

***

#### **Decryption & Decompression Process**

1. **Decode Base64**:
   * Outer string → JSON
2. **Extract Payload**:
   * Decode key, IV, data fields from JSON (Base64 → bytes)
3. **Decrypt**:
   * Use AES-CBC with key & IV to decrypt data → compressed bytes
4. **Decompress**:
   * GZipDecoder on decrypted bytes → UTF-8 JSON
5. **Deserialize**:
   * Parse JSON to Dart Map

***

## Key Classes&#x20;

#### **P2P Communication**

* `NearbyConnectionManager`
  * Handles advertising, discovery, connection, and data transfer
* `ConnectionStrategy`
  * Enum: `P2P_CLUSTER`, `P2P_STAR`, `P2P_POINT_TO_POINT`, `WI_FI_P2P`
* `ConnectionEventListener`
  * Handles state changes, errors, and received bytes

#### **Secure Payload Handling**

* `SecurePayloadCompressor`
  * `compress(Map data): List<int>`
  * `decompress(List<int> compressed): Map`
* `AESCipher`
  * `encrypt(List<int> data, key, iv): List<int>`
  * `decrypt(List<int> encrypted, key, iv): List<int>`
* `Base64PayloadEncoder`
  * `encode(key, iv, data): String`
  * `decode(String): (key, iv, data)`

***

## Data Flow: Send/Receive Sequence

1. **Sender:**
   * Serialize Map → JSON → UTF-8 bytes
   * Compress (GZip) → compressed bytes
   * Generate AES key & IV
   * Encrypt (AES-CBC) compressed bytes → encrypted bytes
   * Base64-encode (key, IV, encrypted) → JSON → Base64-encode JSON
   * Send over a P2P connection
2. **Receiver:**
   * Receive Base64-encoded string
   * Base64-decode → JSON → extract key, IV, encrypted data
   * AES decrypt → compressed bytes
   * GZip decompress → JSON string
   * Parse JSON → Map

***

## Sequence Diagram

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcUNyNdUCQYj-LqoabXp4uGBuXyKpmNvxJHn_-BDL2o87E6gBJtH8idClLhUXk3CgSYhf-2rtSAM_qUJa0CoCeRXH0nzRJyFNPNs62x1qvJUMjw956xqb_py6n9tdJXlB7vyGs8ig?key=h6xj56uLHjrcNj0msKKRCQ" alt=""><figcaption></figcaption></figure>
