# Użyj oficjalnego obrazu MariaDB jako obrazu bazowego
FROM mariadb:latest

# Ustaw zmienne środowiskowe
ENV MYSQL_ROOT_PASSWORD=prestashop
ENV MYSQL_DATABASE=prestashop
ENV MYSQL_USER=prestashop
ENV MYSQL_PASSWORD=prestashop

# Skopiuj plik konfiguracyjny my.cnf (opcjonalne)
# COPY my.cnf /etc/mysql/my.cnf

# Skopiuj pliki inicjalizacyjne (opcjonalne)
# COPY ./initdb.d /docker-entrypoint-initdb.d

# Ustaw domyślny punkt wejścia (nie zmieniaj, jeśli korzystasz z oficjalnego obrazu)
ENTRYPOINT ["docker-entrypoint.sh"]

# Ustaw domyślny komendę do uruchomienia MariaDB
CMD ["mysqld"]

# Otwórz port 3306 dla połączeń do bazy danych
EXPOSE 3306