# 🗝️ Vaultwarden – beginner friendly Docker Compose setup

This repository contains a self-hosted **Vaultwarden** setup using **Docker Compose**.  
Vaultwarden is a lightweigh, open source password manager for all your needs. It is an implementation of the **Bitwarden server API**, written in Rust.  
This configuration supports  **Fedora** or any **SELinux-enabled** Linux distribution, with disk encryption.

---

## 🧩 Features

- Simple Docker Compose deployment
- Persistent local storage
- Works with SELinux out-of-the-box (`:Z` mount label)
- Ready for localhost or LAN deployments
- Easy to extend with Caddy or NGINX for HTTPS

---

## ⚙️ Initial setup

Clone this repository. The directory structure will be

    vaultwarden-docker-compose/
    ├── docker-compose.yml
    ├── .env
    └── README.md
    ├── data
        ├── (files created by container)

Then copy or move the ```.env-example``` to ```.env``` and make your changes. Your .env will be ignored by git.

If everything is correct run your container with ```docker compose up -d ``` and enter the UI. My default is https://localhost:8080. 

---

## ⚠️ Common issues
You can run into issues with permissions on Fedora-based systems or setups with SELinux even if you are in the docker group. To fix this try:

	sudo chown -R 1000:1000 vaultwarden-docker-compose
	chmod -R u+rwX vaultwarden-docker-compose

restart Vaultwarden and check the logs with ```docker compose logs```

If you still have issues run ```sudo chcon -Rt svirt_sandbox_file_t vaultwarden-docker-compose```

Now restart your Vaultwarden again and it should create files inside ```vaultwarden-docker-compose/data```.

---

## 🌐 Vaultwarden GUI setup
(coming soon)
