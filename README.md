# aztec0.87.2
# 🔃 Update Sequencer Node (Aztec)

We normally use the Docker image:  
`aztecprotocol/aztec:alpha-testnet:latest`  
But sometimes, the team recommends switching to an older version when the latest build is unstable.

**Right now, I’ve switched the node to a downgraded version:**  
`aztecprotocol/aztec:0.87.2`

📢 Make sure to monitor Discord for updates about when the latest version becomes stable again.

---

## 1️⃣ Stop the Running Node

### 🔸 For CLI:
```bash
docker stop $(docker ps -q --filter "ancestor=aztecprotocol/aztec") \
&& docker rm $(docker ps -a -q --filter "ancestor=aztecprotocol/aztec")

screen -ls | grep -i aztec | awk '{print $1}' | xargs -I {} screen -X -S {} quit
```

### 🔸 For Docker:
```bash
cd aztec
docker compose down
```

---

## 2️⃣ Update the Node Version

### 🔹 If you're using CLI:
```bash
aztec-up -v 0.87.2
```

### 🔹 If you're using Docker:
```bash
cd aztec
nano docker-compose.yml
```

Update the image line:
```yaml
image: aztecprotocol/aztec:alpha-testnet
```
Replace it with:
```yaml
image: aztecprotocol/aztec:0.87.2
```

---

## 3️⃣ Delete Old Node Data
```bash
rm -rf ~/.aztec/alpha-testnet/data/
```

---

## 4️⃣ Re-run the Node

Once done, just run your node again like usual.

---

## 🔁 Switching Back to the Latest Version (When It's Stable)

Once the team confirms stability on Discord:

### 🔄 For Docker:
```yaml
image: aztecprotocol/aztec:alpha-testnet
```

### 🔄 For CLI:
```bash
aztec-up alpha-testnet
```

---

## 📌 Final Notes
- Always follow the official Aztec Discord for version updates.
- Until the latest build is stable, stick to `0.87.2` as recommended.
