# Konfiguracja bazowa Ansible

## OPIS

Jest to przykład bazowej konfiguracji środowiska trzech hostów, uruchomionych za pomocą Vagrant/Virtualbox. Idea jest taka, żeby skonfigurować automatycznie odpowiednich użytkowników i skopiować na wszystkie hosty klucz SSH.

Uruchomienie środowiska odbywa się w dwóch krokach:

1. Konfiguracja Virtualbox za pomocą Vagrant
2. Konfiguracja hostów za pomocą Ansible

## **JAK URUCHOMIĆ ŚRODOWISKO**

**Krok 1:**

1. Skopiuj plik Vagrantfile do lokalnego, pustego katalogu na stacji roboczej
2. Otwórz plik Vagrantfile i ustaw odpowiednie zmienne
   - `ETH_DEV` - do którego interfejsu ma być przypisany interfejs `eth1` hostów
   - Lista interfejsów: `c:\Program Files\Oracle\VirtualBox\VBoxManage.exe" list bridgedifs`
3. Uruchom `vagrant up`
4. Zaloguj się za pomocą SSH do każdego hosta (*cicd*, *node1*, *node2*), jako *vagrant/vagrant*, używając polecenia:
   - `vagrant ssh <host>`
5. Pozyskaj adres IP interfejsu `eth1` za pomocą polecenia:
   - `ip addr`

**Krok 2:**

1. Zaloguj się za pomocą SSH do hosta *cicd*, jako *vagrant/vagrant*, używając polecenia:
   - `vagrant ssh cicd`
2. Sklonuj poniższe repozytorium za pomocą polecenia:
   - `git clone git@github.com:netdevopspl/securecrt-runcommands.git`
3. Otwórz plik inventory i ustaw odpowiednie zmienne (adresy IP)
4. Uruchom playbook za pomocą polecenia:
   - `ansible-playbook setup.yml`
5. Zaloguj się za pomocą SSH do hosta *cicd*, jako użytkownik *devops/devops*, najlepiej już za pomocą lepszego terminala
6. Powinieneś mieć dostęp do wszystkich hostów za pomocą klucza SSH
7. Można rozpocząć zabawę z Ansible
    - Używaj konta *devops/devops*

## **WYMAGANIA**

1. Zainstalowany Virtualbox
2. Zainstalowany Vagrant
3. (opcjonalnie) Zainstalowany Git

## OGRANICZENIA

Vagrant powołuje trzy hosty Linux Centos. Jeżeli dystrybucja zostanie zmieniona na inną, to konieczna będzie modyfikacja Vagrantfile, a dokładnie początkowego provision za pomocą `shell` - zamiana `yum` na `apt-get`

## TODO

W przyszłości planuję zamienić provision `shell` na `ansible`

## **KONTAKT**

E-mail: [krzysztof@nowoczesnysieciowiec.pl](mailto:krzysztof@nowoczesnysieciowiec.pl?Subject=Projekt%20VagrantAnsibleSetup)

## **LICENCJA**

Autor dołożył wszelkich starań, aby zawarte tu informacje były rzetelne, ale nie gwarantuje ich poprawności. Autor nie bierze odpowiedzialności za żadne szkody wynikające z wykorzystania zawartych tu informacji i skryptów.

Pliki zawarte w tym projekcie mogą być swobodnie wykorzystywane. Mogą one być też dowolnie modyfikowane, z zachowaniem informacji o źródle.

Kopiowanie i dystrybucja możliwa jest tylko z zachowaniem informacji o źródle.

Zawarte w tym projekcie nazwy produktów i znaki towarowe należą do ich prawowitych właścicieli

(C) [Nowoczesny Sieciowiec](https://nowoczesnysieciowiec.pl "Blog Nowoczesny Sieciowiec"), 2021
