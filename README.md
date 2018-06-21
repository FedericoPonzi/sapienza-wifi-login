Questi semplici script permettono di eseguire il login in automatico una volta connessi all'ssid della rete wifi "sapienza" o "colossus".

# Requisiti

 * bash
 * python3, con la libreria requests (installabile con `pip3 install requests --user`)

# Installazione

 1 Scaricare il repository: `git clone `
 2 Modificare in `sapienza_login` il dizionario `login_data` con i nostri username e password per accedere alla rete
 3 Spostare sapienza_login in ~/.local/sapienza_login (o dove preferiamo) e dare permessi di esecuzione: `chmod +x sapienza_login`
 4 Spostare `00_sapienza` in `/etc/NetworkManager/dispatcher.d/00_sapienza`, cambiare ownership e dare permessi di esecuzione: `sudo chown root:root 00_sapienza && sudo chmod +x 00_sapienza`

That's it!
