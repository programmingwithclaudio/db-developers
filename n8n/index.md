
### NGROK LOCAL

- [https://dashboard.ngrok.com/](https://dashboard.ngrok.com/ )
```bash
curl -sSL https://ngrok-agent.s3.amazonaws.com/ngrok.asc \
	| sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null \
	&& echo "deb https://ngrok-agent.s3.amazonaws.com buster main" \
	| sudo tee /etc/apt/sources.list.d/ngrok.list \
	&& sudo apt update \
	&& sudo apt install ngrok
```
- REVISA U INGRESA EL COMANDO  
```BASH
ngrok config add-authtoken XXXXXXXXXXXXXX
# APROBADO
ngrok http http://localhost:5678/
```


### Referencias
- [youtube-ngrok](https://www.youtube.com/watch?v=A5fxVzblbtA)