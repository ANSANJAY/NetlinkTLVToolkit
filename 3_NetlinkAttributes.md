
# 📝 Netlink Attributes: An Overview 🚀

## 📌 Introduction:

### 🔍 Background:
- So far, we've set up basic **Netlink socket-based communication** between user space and kernel space.
- The **Netlink protocol** demands the use of the TLV (Type-Length-Value) format for data exchange.

### 🎯 Structure of Netlink Data:
- The Netlink message starts with the **Netlink message header**.
- Following the header, there's a **payload**, which should be in the form of discrete TLVs.
- Example: A payload formatted in four TLVs.

## 📌 TLV in the Context of Netlink:

### 🔍 Basic Anatomy:
- Each TLV can have a variable size.
- Three components: **Type**, **Length**, and **Value**.
- For Netlink, the **Type** and **Length** fields occupy **two bytes** each (instead of the typical one byte).

### 🎯 Netlink Attribute Data Structure:
- Netlink APIs offer a structure called **Netlink attribute** for defining the Netlink type and length.
- Each of these (type and length) is 16 bits or two bytes.
- The **Value** part can vary in size.
- Example: TLV with length of 32 bytes, type code 2, and its value. Another TLV with length of 64 bytes, type code 3, and its value.

### 🔎 Interpretation of TLVs:
- The recipient (either user space or kernel space) must know how to interpret TLV codes.
- If the recipient doesn't recognize a TLV code, they should skip it.
- The standardized format: A Netlink message header followed by a payload formatted in TLVs.

## 📌 Interaction with Linux Kernel:

### 🔍 Linux Kernel APIs:
- Linux provides macros for working with Netlink headers and TLVs.
- Detailed exploration of these macros will be in the programming section.

### 🎯 Cascading Netlink Messages:
- A unique feature of Netlink messages: they can be **cascaded**.
- A new Netlink message header can be appended right after the payload of the first Netlink message header.
- These cascaded messages can be exchanged in any direction between user space and kernel space.

---

## 🤔 Interview Questions about Netlink Attributes:

1. **Question**: What is the role of the Netlink protocol in kernel-user space communication?

   **Answer**: The Netlink protocol facilitates socket-based communication between user space and kernel space, allowing for the exchange of data in the TLV (Type-Length-Value) format.

2. **Question**: How are TLVs structured in the context of the Netlink protocol?

   **Answer**: In Netlink, each TLV has the Type and Length fields occupying two bytes each, followed by a variable-sized Value field.

3. **Question**: What action should be taken if a recipient encounters an unrecognized TLV code?

   **Answer**: If the recipient does not recognize a TLV code, they should simply skip it, ensuring robustness in communication.

4. **Question**: Describe the concept of cascading in the context of Netlink messages.

   **Answer**: Cascading in Netlink messages refers to the ability to append a new Netlink message header right after the payload of a preceding message. This feature allows for a sequence of messages to be communicated seamlessly.

---

I hope this helps with your preparation! 🌟📘
