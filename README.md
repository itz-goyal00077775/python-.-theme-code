# python--theme-code
: ["lightblue", "skyblue"],
        "Snowy": ["white", "lightcyan"],
        "Tropical": ["lightgreen", "palegreen"]
    }import tkinter as tk
import random

def get_climate(place):
    """Simulates getting climate data (replace with real API)."""
    climates = {
        "Sunny": ["yellow", "lightgoldenrod"],
        "Cloudy": ["gray80", "gray60"],
        "Rainy": ["lightblue", "skyblue"],
        "Snowy": ["white", "lightcyan"],
        "Tropical": ["lightgreen", "palegreen"]
    }
    # For simplicity, we randomly choose a climate
    return random.choice(list(climates.keys()))

def change_theme(place, widgets):
    """Changes the background theme based on climate."""
    climate = get_climate(place)
    climates = {
        "Sunny": ["yellow", "lightgoldenrod"],
        "Cloudy": ["gray80", "gray60"],
        "Rainy"
    bg_colors = climates[climate]
    for widget_name, widget in widgets.items():
        if widget_name == "window":
            widget.config(bg=bg_colors[0])
        else:
            widget.config(bg=bg_colors[1], fg="black") #keep text black for visibility.
    print(f"Theme changed to {climate} for {place}")

# Create the main window
window = tk.Tk()
window.title("Climate Theme App")
window.geometry("300x200")

# Create a label for place input
place_label = tk.Label(window, text="Enter Place:")
place_label.pack(pady=10)

# Create an entry for place input
place_entry = tk.Entry(window)
place_entry.pack(pady=5)

# Create a button to change the theme
def update_theme():
  place = place_entry.get()
  widgets = {"window": window, "label": label, "place_label": place_label, "place_entry": place_entry, "theme_button": theme_button}
  change_theme(place, widgets)

theme_button = tk.Button(window, text="Change Theme", command=update_theme)
theme_button.pack(pady=10)

# Create a label
label = tk.Label(window, text="Climate Theme App")
label.pack(pady=20)

# Initialize with a default theme
widgets = {"window": window, "label": label, "place_label": place_label, "place_entry": place_entry, "theme_button": theme_button}
change_theme("Default", widgets) #Initial theme

window.mainloop() 


