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
