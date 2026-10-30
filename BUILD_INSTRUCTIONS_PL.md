# Regrowth – natywny port NeoForge 26.1.2, DEV3

To projekt **niezweryfikowany kompilacją**, nie gotowy mod. Nie wymaga Sinytra ani Fabric do budowania.

## Próba kompilacji na komputerze z internetem
1. Zainstaluj JDK 25 i Gradle 9.8.2.
2. Wejdź do katalogu projektu.
3. Uruchom `gradle --no-configuration-cache --stacktrace build`.
4. Jeśli budowa przejdzie, sprawdź `build/libs/`. Jeśli nie, zachowaj pełny log.

## Alternatywa: GitHub Actions
Wgraj zawartość tego katalogu do repozytorium GitHub, otwórz Actions -> Build Regrowth NeoForge 26.1.2 (experimental) -> Run workflow. Workflow pobiera zależności na serwerach GitHub, a następnie udostępnia logi lub JAR. Samo uruchomienie workflow **nie gwarantuje** kompilacji, bo port kodu nie jest jeszcze ukończony.

## Zidentyfikowane obszary potencjalnych błędów migracji
- `modloader/events/HandleNeoForgeEntityMoveEvent.java`: `EntityTickEvent.Pre` i dostęp do poziomu/pozycji.
- `modloader/events/TrampleEventHandler.java`: `BlockEvent.FarmlandTrampleEvent`.
- `modloader/config/MyConfig.java`: API rejestracji konfiguracji i obsługa zdarzeń.
- `actions/*`: zmiany nazw i sygnatur API Minecraft od 1.21.11 do 26.1.2.

## Blokada w środowisku ChatGPT
Nie działa rozwiązywanie DNS `maven.neoforged.net`; Gradle nie może uzyskać `net.neoforged.moddev:2.0.148`. Przez to nie otrzymaliśmy nawet diagnostyki kompilatora Java. Problem jest niezależny od działania lokalnego JDK 25 i Gradle 9.8.2.
