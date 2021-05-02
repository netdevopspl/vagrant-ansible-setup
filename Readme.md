# Konfiguracja bazowa Ansible

Jest to przykład bazowej konfiguracji środowiska trzech hostów, uruchomionych za pomocą Vagrant/Virtualbox

## **JAK URUCHOMIĆ ŚRODOWISKO**

1. Skopiuj plik Vagrantfile do lokalnego katalogu na stacji roboczej
2. Otwórz plik Vagrantfile i ustaw odpowiednie zmienne
3. Uruchom `vagrant up`
4. Zaloguj się za pomocą SSH do hosta cicd, jako `vagrant/vagrant`, używając polecenia:
   - `vagrant ssh cicd`
5. Sklonuj poniższe repozytorium za pomocą polecenia:
   - `git clone git@github.com:netdevopspl/securecrt-runcommands.git`
6. Otwórz plik inventory i ustaw odpowiednie zmienne

## **WYMAGANIA**

1. Zainstalowany Virtualbox
2. Zainstalowany Vagrant

## **KONTAKT**

E-mail: [krzysztof@nowoczesnysieciowiec.pl](mailto:krzysztof@nowoczesnysieciowiec.pl?Subject=Projekt%20RunAndCompareCommands)

## **LICENCJA**

Autor dołożył wszelkich starań, aby zawarte tu informacje były rzetelne, ale nie gwarantuje ich poprawności. Autor nie bierze odpowiedzialności za żadne szkody wynikające z wykorzystania zawartych tu informacji i skryptów.

Pliki zawarte w tym projekcie mogą być swobodnie wykorzystywane. Mogą one być też dowolnie modyfikowane, z zachowaniem informacji o źródle.

Kopiowanie i dystrybucja możliwa jest tylko z zachowaniem informacji o źródle.

Zawarte w tym projekcie nazwy produktów i znaki towarowe należą do ich prawowitych właścicieli

(C) [Nowoczesny Sieciowiec](https://nowoczesnysieciowiec.pl "Blog Nowoczesny Sieciowiec"), 2021
