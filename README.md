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



---

## day 5:

```python

# -*- coding: utf-8 -*-
from itertools import product

def xor_bytes(data1, data2):
    return bytes(a ^ b for a, b in zip(data1, data2))

def clean_byte_string(byte_data):
    cleaned = byte_data.replace(b'\x00', b' ')
    return cleaned.decode('utf-8', errors='ignore')

def main():
    message1_path = 'message1.enc'
    message2_path = 'message2.enc'

    with open(message1_path, 'rb') as f:
        message1 = f.read()
    with open(message2_path, 'rb') as f:
        message2 = f.read()

    if len(message1) != len(message2):
        print("Fehler: Die Nachrichten sind nicht gleich lang!")
        return

    xor_result = xor_bytes(message1, message2)
    print(f"\nXOR-Ergebnis (als Bytes):\n{xor_result}")

    cleaned_text = clean_byte_string(xor_result)
    print("\nBereinigte Nachricht:")
    print(cleaned_text)

if __name__ == "__main__":
    main()

```

---

## day 6:

//

---

## day 7:

//

---

## day 8:

![{73D1F291-DED2-4432-A0F9-B5D791CEB775}](https://github.com/user-attachments/assets/4318242d-6908-4aac-a207-6974ce143514)


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kerzenkreis</title>
    <style>
        body { font-family: Arial; text-align: center; }
        .circle { position: relative; width: 300px; height: 300px; margin: auto; }
        .candle { position: absolute; width: 40px; height: 40px; border-radius: 50%; display: flex; justify-content: center; align-items: center; }
        .lit { background: #ffc107; }
    </style>
</head>
<body>
<h1>Kerzenkreis</h1>
<div id="circle" class="circle"></div>
<div id="info"></div>
<button id="next">Weiter</button>
<script>
    const total = 24, candles = Array(total).fill(0); let current = 1, day = 1; candles[current] = 1;
    const circle = document.getElementById("circle"), angle = 2 * Math.PI / total;
    [...Array(total)].forEach((_, i) => {
        const c = document.createElement("div");
        c.className = "candle"; c.style.left = `${140 + 120 * Math.cos(i * angle)}px`;
        c.style.top = `${140 + 120 * Math.sin(i * angle)}px`; c.textContent = i + 1; circle.appendChild(c);
    });
    const update = () => {
        document.querySelectorAll(".candle").forEach((c, i) => c.classList.toggle("lit", candles[i]));
        document.getElementById("info").textContent = `Tag ${day}: Kerze ${current + 1}`;
    };
    document.getElementById("next").onclick = () => {
        if (day >= total) return;
        let skip = 0; while (skip < 2) current = (current + 1) % total, skip += !candles[current];
        candles[current] = 1; day++; update();
    };
    update();
</script>
</body>
</html>
```

---
