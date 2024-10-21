# 1.2 Instalación de zonas mestras primarias en Windows Server

1. Instala o servidor DNS no equipo lukeskywalker. Comproba que xa funciona coma servidor DNS caché pegando no documento de entrega a saída deste comando  nslookup -norecurse www.starwars.com localhost

![Captura1](imaxes/Captura1.png)

2. Configura o servidor DNS para que empregue como reenviador 8.8.8.8. pegando no documento de entrega a captura de pantalla da configuración do reenviador e a saída deste comando: nslookup -recurse www.starwars.com localhost

![Captura2](imaxes/Captura2.png)
![Captura3](imaxes/Captura3.png)

3. Instala unha zona primaria de resolución directa chamada "academia.jedi" e engade os seguintes rexistros de recursos (a maiores dos rexistros NS e SOA imprescindibles):

    Tipo A: lukeskywalker con IP 192.168.20.101

    Tipo A: benskywalker con IP 192.168.20.102

    Tipo A: obiwankenobi con IP 192.168.56.152 e 192.168.56.153

    Tipo A: hansolo con IP 192.168.56.105

    Tipo A: leia con IP 192.168.56.106

    Tipo A: anakinsolo con IP 192.168.56.106

    Tipo CNAME mestrejedi a obiwankenobi

    TIPO MX con prioridade 10 sobre o equipo hansolo

    TIPO TXT "thon" con "un Jedi debe sentir a tensión entre os dous lados da Forza"

    TIPO NS con benskywalker

    Pega no documento de entrega a captura dos rexistros creados

![Captura4](imaxes/Captura4.png)

4. Instala unha zona de resolución inversa que teña que ver co enderezo do equipo lukeskywalker, e engade rexistros PTR para os rexistros tipo A do exercicio anterior. Pega no documento de entrega o a captura dos rexistros da zona.

![Captura5](imaxes/Captura5.png)

5. Comproba que podes resolver os distintos rexistros de recursos. Pega no documento de entrega a saída dos comandos:

- nslookup lukeskywalker.academia.jedi localhost
![Captura6](imaxes/Captura6.png)
- nslookup hansolo.academia.jedi localhost
![Captura7](imaxes/Captura7.png)
- nslookup leia.academia.jedi localhost
![Captura8](imaxes/Captura8.png)
- nslookup anakinsolo.academia.jedi localhost
![Captura9](imaxes/Captura9.png)
- nslookup academia.jedi localhost
![Captura10](imaxes/Captura10.png)
- nslookup -q=mx academia.jedi localhost
![Captura11](imaxes/Captura11.png)
- nslookup -q=ns academia.jedi localhost
![Captura12](imaxes/Captura12.png)
- nslookup -q=soa academia.jedi localhost
![Captura13](imaxes/Captura13.png)
- nslookup -q=txt thon.academia.jedi localhost
![Captura14](imaxes/Captura14.png)
- nslookup 192.168.56.101 localhost
![Captura15](imaxes/Captura15.png)
