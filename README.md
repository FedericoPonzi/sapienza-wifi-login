Questi semplici script permettono di eseguire in automatico il login al captive portal una volta connessi all'ssid delle reti wifi "sapienza" e "colossus".

## Requisiti

 * `bash`
 * `python3`, con la libreria requests (installabile con `pip3 install requests --user`)
 * `iwgetid`, utilizzato per avere il nome della rete wifi.

## Installazione

 1. Scaricare il repository: `git clone https://github.com/FedericoPonzi/sapienza-login`
 2. Modificare in `sapienza_login` il dizionario `login_data` con username e password per accedere alla rete
 3. Spostare `sapienza_login` in `~/.local/bin/sapienza_login` (ad esempio) e dare permessi di esecuzione: `chmod +x sapienza_login`
 4. Modificare la variable LOGIN_SCRIPT in `00_sapienza` in modo che punti alla path di `sapienza_login`.
 4. Spostare `00_sapienza` in `/etc/NetworkManager/dispatcher.d/00_sapienza`, cambiare ownership e i permessi: `sudo chown root:root 00_sapienza && sudo chmod 755 00_sapienza`

## Testing
Per testare lo script, prima dovremo riavviare il network-manager:

    sudo systemctl restart network-manager
 
E connetterci alla rete `sapienza` o `colossus`.

## About
`00_sapienza` utilizza il [NetworkManager dispatcher](https://wiki.archlinux.org/index.php/NetworkManager). Quando ci connettiamo ad un ssid con nome colossus o sapienza, viene eseguito lo script python che tenta di eseguire il login al captive portal inviando una richiesta `POST`.
