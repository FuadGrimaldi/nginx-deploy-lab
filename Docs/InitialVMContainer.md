## Run this every docker compose is restart

docker exec -i target-vm bash -c "cat >> /home/deploy/.ssh/authorized_keys" < ~/.ssh/id_ed25519.pu
docker exec -it target-vm chown -R deploy:deploy /home/deploy/.ssh
docker exec -it target-vm chmod 700 /home/deploy/.ssh
docker exec -it target-vm chmod 600 /home/deploy/.ssh/authorized_keys

ssh -p 2222 deploy@localhost
