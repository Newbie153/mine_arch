sudo pacman -S git hyprland kitty

Для hyprland

cd ~
git clone https://github.com/Newbie153/mine_arch.git

# Делаем бэкап старого конфига, если он есть
mv ~/.config/hypr ~/.config/hypr_backup 

# Создаем ссылку (путь к репо -> куда привязать)
ln -s ~/mine_arch/hypr ~/.config/hypr

Для Kitty
# Создаем папку для конфигов, если её нет
mkdir -p ~/.config/kitty

# Привязываем только файл конфига
ln -s ~/mine_arch/kitty/kitty.conf ~/.config/kitty/kitty.conf

chmod +x ~/mine_arch/scripts/*



waybar чисто чтоб пользоваться можно было 

в ~/.config/waybar/config:
{
    "layer": "top",
    "position": "top",
    "height": 36,
    "margin-top": 5,
    "margin-left": 10,
    "margin-right": 10,
    "spacing": 10,

    "modules-left": ["clock"],
    "modules-center": ["hyprland/workspaces"],
    "modules-right": ["pulseaudio", "network", "cpu", "tray"],

    "hyprland/workspaces": {
        "format": "{name}",
        "on-click": "activate",
        "all-outputs": true
    },

    "clock": {
        "format": " {:%H:%M     %d.%m}",
        "tooltip-format": "<tt><small>{calendar}</small></tt>"
    },

    "cpu": {
        "interval": 2,
        "format": " {usage}%"
    },

    "network": {
        "format-wifi": "",
        "format-disconnected": "  ",
        "tooltip-format": "{essid}"
    },

    "pulseaudio": {
        "format": "{icon} {volume}%",
        "format-icons": ["", ""]
    },

    "tray": {
        "icon-size": 16,
        "spacing": 10
    }
}

в ~/.config/waybar/style.css:

/* Основной шрифт */
* {
    border: none;
    font-family: "JetBrainsMono Nerd Font", "Roboto", "Arial";
    font-size: 13px;
    min-height: 0;
}

/* Прозрачный фон панели */
window#waybar {
    background: transparent;
}

/* Стили для модулей-пилюль (Лево и Право) */
#clock, #pulseaudio, #network, #cpu, #tray {
    background-color: #1e1e2e; /* Цвет Catppuccin Mocha */
    color: #cdd6f4;
    border-radius: 20px;
    padding: 0 15px;
    margin: 0 2px;
    border: 1px solid #313244;
}

/* СТИЛЬ КРУГЛЫХ КНОПОК (Центр) */
#workspaces {
    background: transparent;
    margin: 0;
    padding: 0;
}

#workspaces button {
    background-color: #1e1e2e;
    color: #cdd6f4;
    border: 1px solid #89b4fa; /* Цвет контура */
    border-radius: 50%;
    margin: 0 4px;
    padding: 0;
    
    /* Идеальный круг */
    min-width: 32px;
    max-width: 32px;
    min-height: 32px;
    max-height: 32px;
    
    transition: all 0.3s ease;
}

#workspaces button.active {
    background-color: #89b4fa; /* Цвет активного круга */
    color: #11111b;
    border-color: #89b4fa;
    min-width: 34px; /* Легкое увеличение активного */
    min-height: 34px;
}

#workspaces button:hover {
    background-color: rgba(137, 180, 250, 0.2);
    box-shadow: 0 0 10px rgba(137, 180, 250, 0.4);
}

/* Индивидуальные цвета для красоты */
#clock { color: #cba6f7; }
#cpu { color: #fab387; }
#pulseaudio { color: #89b4fa; }
#network { color: #a6e3a1; }
