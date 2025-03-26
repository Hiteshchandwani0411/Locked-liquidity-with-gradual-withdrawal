# **Locked Liquidity Smart Contract**  

## **1. Title**  
**Locked Liquidity with Gradual Withdrawal**  

## **2. Description**  
The **Locked Liquidity Smart Contract** is a Move-based module deployed on the **Aptos blockchain** that allows users to **lock liquidity (AptosCoins)** and withdraw funds **gradually** over time. Instead of allowing instant access to all funds, this contract enforces controlled withdrawal, ensuring stability and long-term liquidity management.  

### **Key Features:**  
✅ **Liquidity Locking** – Users can deposit AptosCoins into a locked pool.  
✅ **Gradual Withdrawal** – Withdraw **10% of locked funds per transaction**.  
✅ **Secure & Transparent** – Only the **owner** of locked funds can withdraw.  
✅ **Efficient Storage** – Uses Move’s `move_to` and `borrow_global_mut` for optimized data management.  

---

## **3. Vision**  
The **goal** of this contract is to provide a **trustless** and **transparent** liquidity locking mechanism that prevents rug pulls, promotes long-term commitment in DeFi projects, and ensures that locked funds are released in a **controlled and gradual manner**.  

This can be especially useful for:  
- **Liquidity Providers (LPs)** to lock tokens in liquidity pools.  
- **Vesting Contracts** where funds are unlocked periodically.  
- **DeFi Platforms** requiring controlled fund release.  

---

## **4. Future Scope**  
While the current implementation allows fixed **10% withdrawals**, future versions could introduce:  
- **Customizable withdrawal percentages** (e.g., based on time or conditions).  
- **Time-based unlocking mechanism** (e.g., funds released after X days).  
- **Multi-user liquidity pools** with multiple contributors.  
- **Automatic scheduled withdrawals** to enhance usability.  
- **Integration with governance mechanisms** for flexible fund release.  

---

## **5. Contract Details**  

### **Module Name:**  
`MyModule::LockedLiquidity`  

### **Functions:**  
#### **1. Lock Liquidity**  
```move
public fun lock_liquidity(owner: &signer, amount: u64)
```
- Deposits `amount` of AptosCoins from the **owner’s wallet** into a locked liquidity pool.  
- Stores the locked amount in a **LiquidityPool** resource under the owner’s account.  

#### **2. Withdraw Liquidity Gradually**  
```move
public fun withdraw(owner: &signer) acquires LiquidityPool
```
- Allows the **owner** to withdraw **10%** of their locked liquidity per call.  
- Updates the remaining locked balance accordingly.  

### **Structs:**  
#### **LiquidityPool**  
```move
struct LiquidityPool has key, store {
    owner: address,
    total_locked: u64,
}
```
- Stores the **owner’s address** and **total locked funds**.  

### **Security & Access Control:**  
- **Only the owner** of the `LiquidityPool` can withdraw funds.  
- Uses **Aptos standard coin module** for secure token handling.  

---

## **Conclusion**  
The **Locked Liquidity Smart Contract** offers a **secure, transparent, and controlled** liquidity management solution, perfect for DeFi projects and long-term financial commitments. With future enhancements, it can become a **key building block** for vesting schedules, staking platforms, and liquidity management systems in the **Aptos ecosystem**.  

## Contract address
0x30393672cbf4d6b3dacd2e70ded2499e415de204993c31911eea179dfd641e3f

![image](https://github.com/user-attachments/assets/c3b3b0eb-1ed3-4fc9-867e-c5479f2be8dd)
