# Aztec-network

# Aztec Network - Hướng Dẫn Thiết Lập Node Sequencer (Testnet Sepolia)

## 📋 Yêu Cầu Hệ Thống

* Hệ điều hành: Ubuntu 20.04 hoặc 22.04
* CPU: 8 lõi
* RAM: 16GB
* Ổ cứng: SSD 100GB+
* Kết nối internet ổn định
* Ví Ethereum với ETH trên testnet Sepolia([GitHub][1], [Aztec Documentation][2], [GitHub][3])

## ⚙️ Cài Đặt

### 1. Cập nhật hệ thống và cài đặt các gói cần thiết

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl git unzip build-essential -y
```

### 2. Cài đặt Node.js (phiên bản 18 LTS)

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
node -v
```

### 3. Cài đặt Aztec CLI

```bash
bash -i <(curl -s https://install.aztec.network)
aztec-up alpha-testnet
```

### 4. Thiết lập biến môi trường

Tạo file `.env` và thêm các biến sau:

```bash
L1_RPC_URLS=https://rpc.ankr.com/eth_sepolia/your_api_key
VALIDATOR_PRIVATE_KEY=0xYOUR_PRIVATE_KEY
ATTESTER_ADDRESS=0xYOUR_ATTESTER_ADDRESS
PROPOSER_EOA=0xYOUR_PROPOSER_EOA
STAKING_ASSET_HANDLER=0xF739D03e98e23A7B65940848aBA8921fF3bAc4b2
L1_CHAIN_ID=11155111
```

**Lưu ý:** Không chia sẻ khóa riêng tư của bạn.

### 5. Thêm L1 Validator

```bash
aztec add-l1-validator \
  --l1-rpc-urls $L1_RPC_URLS \
  --private-key $VALIDATOR_PRIVATE_KEY \
  --attester $ATTESTER_ADDRESS \
  --proposer-eoa $PROPOSER_EOA \
  --staking-asset-handler $STAKING_ASSET_HANDLER \
  --l1-chain-id $L1_CHAIN_ID
```

### 6. Khởi động node Sequencer

```bash
aztec start --node --archiver --sequencer --network alpha-testnet
```

## 🧪 Kiểm Tra Hoạt Động

* Kiểm tra logs để đảm bảo node đang hoạt động bình thường.
* Sử dụng các công cụ như `curl` hoặc trình duyệt để kiểm tra các endpoint nếu cần.

## 📞 Hỗ Trợ Cộng Đồng

* Discord chính thức của Aztec: [https://discord.gg/aztec](https://discord.gg/aztec)
* Twitter/X: [https://x.com/aztecnetwork](https://x.com/aztecnetwork)




