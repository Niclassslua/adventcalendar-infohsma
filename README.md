# adventcalendar-infohsma
Lösungen zu dem 2024er Adventskalender der Informatik Fakultät Hochschule Mannheim

Ich lade hier meine Lösungen zum Adventskalender der Informatik Fakultät Hochschule Mannheim aus dem Jahr 2024 hoch.

## day 1:

/


---


## day 2:

Gegebenes Foto:

![IMG_1735](https://github.com/user-attachments/assets/58a9d185-1460-4701-8189-058be5f2de5e)

Invertiertes Invertiertes Foto:

![IMG_1736](https://github.com/user-attachments/assets/48efd80e-af7c-4d67-b091-6d3075d6b26c)


Nicht ISO konformes Layout, `delete` Button in oberer rechter Ecke und halb so großer, kreis geprägter `reset` Button auffällig...

Nach etwas gesuche kam ich auf Apple Computer und dann auch auf den `Apple lle` Computer. Damit wiederum auf das Bild der Tastatur aus dem Wikipedia Artikel:

![Applelle_Keyboard](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9f/Apple_IIe.jpg/1280px-Apple_IIe.jpg)

---


## day 3:

```python

from termcolor import colored

# Gegebene ASCII-Art-Zeilen
ascii_lines = [
    "     _____          _    *       __        __",
    "      _ _                *      _     _",
    "          _ |  ___| __ __*_ | |__   ___  \\ \\",
    "        / /__(_) |__  _ _*_   __ _  ___| |__ |",
    "     |_ ___ _ __ | || |_ *| '__/ _ \\| '_ \\ / _",
    "     \\  \\ \\ /\\ / / _ \\ | *'_ \\| '_ \\ / _` |/ _",
    "    ******************************************",
    "    _| '_ \\| __/ _ \\ '_ \\*| ||  _|| | | (_) |",
    "    | | |  __/   \\ V  V /*  __/ | | | | | | |",
    "    (_| | (__| | | | ||  *__/ | | |_||_|  |_|",
    "     \\___/|_| |_\\___|   *  \\_/\\_/ \\___|_|_| |_",
    "     |_| |_\\__,_|\\___|_| *|_|\\__\\___|_| |_(_)"
]


def remove_stars(lines):
    """
    Entfernt Sterne aus den Zeilen.
    Entfernt eine Zeile vollständig, wenn sie nur aus Sternen besteht.
    """
    print(colored("\n1. Entferne nur Sterne oder ganze Zeilen mit nur Sternen:", "yellow"))
    no_star_lines = []
    for line in lines:
        stripped_line = line.strip()
        if stripped_line == "*" * len(stripped_line):  # Zeile enthält nur Sterne
            print(colored(f"Entferne Zeile mit nur Sternen: {line}", "red"))
            continue
        no_star_lines.append(line.replace('*', ''))  # Nur Sterne entfernen
    for line in no_star_lines:
        print(colored(line, "green"))
    return no_star_lines


def add_tabs_to_lines(lines):
    """Fügt Einrückungen (Tabulatoren) hinzu, von unten nach oben abnehmend."""
    print(colored("\n2. Füge Tabulatoren von unten nach oben hinzu:", "yellow"))
    total_lines = len(lines)
    if total_lines == 0:
        print(colored("FEHLER: Keine Zeilen verfügbar für Tabulatoren!", "red", "on_white"))
        return []

    tabbed_lines = [(" " * (4 * (total_lines - i - 1))) + line for i, line in enumerate(lines)]
    for line in tabbed_lines:
        print(colored(line, "blue"))
    return tabbed_lines


def split_even_uneven(lines):
    """Teilt die Zeilen in even (gerade) und uneven (ungerade) auf."""
    print(colored("\n3. Teile die Zeilen in even und uneven auf:", "yellow"))
    if not lines:
        print(colored("FEHLER: Keine Zeilen verfügbar zum Aufteilen!", "red", "on_white"))
        return [], []

    even_lines = [line for i, line in enumerate(lines) if i % 2 == 0]
    uneven_lines = [line for i, line in enumerate(lines) if i % 2 != 0]

    print(colored("\nEven Lines (Gerade Zeilen):", "cyan"))
    for line in even_lines:
        print(colored(line, "green"))

    print(colored("\nUneven Lines (Ungerade Zeilen):", "magenta"))
    for line in uneven_lines:
        print(colored(line, "green"))

    return even_lines, uneven_lines


if __name__ == "__main__":
    print(colored("Start des ASCII-Manipulationsskripts!", "white", "on_blue"))

    # Schritt 1: Entferne Sterne und Zeilen mit nur Sternen
    no_star_lines = remove_stars(ascii_lines)

    # Schritt 2: Füge Tabulatoren von unten nach oben hinzu
    tabbed_lines = add_tabs_to_lines(no_star_lines)

    # Schritt 3: Teile die Zeilen in even und uneven auf
    even_lines, uneven_lines = split_even_uneven(tabbed_lines)
    print(colored("\nFertig manipulierte ASCII-Art Schnipsel", "white", "on_green"))

```

