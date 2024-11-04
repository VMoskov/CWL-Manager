# CWL-Manager
## Clash of Clans Clan War League manager
This is a tool to help manage your clan's CWL roster. It will help you to extract all the players from your clans and then enable you to select and distribute players into their respective clans for the ongoing CWL season. It will also help you keep track of the results of the player performance after the league is finished. Every clan league is supposed to be provided with certain coefficient in order to regulate the stars acquired by players in higher leagues vs lower leagues. This tool will help you to calculate the stars and the final score of each player based on the league they are in.<br>
The tool is written in Python and uses the following libraries:
- pandas
- openpyxl
- Requests

which can be installed to your system using the following command:
```bash
pip install requirements.txt
```

The tool is designed to be used with the help of the command line interface. The tool is divided into 3 main parts:
1. Extracting the players from the clans
2. Distributing the players into the clans
3. Calculating the final score of the players

Points 1 and 2 are supposed to be done using `preprocessing.py` script, while point 3 is supposed to be done using `postprocessing.py` script.<br>

## 1. Extracting the players from the clans
The first step is to extract the players from the clans. This is done using the `preprocessing.py` script. The script will expect to provide the clan tag/clan tags of the clans you want to extract the players from. As of now, tags should be added manually to the script. The script will also expect the API key to be provided, in form of a text file named `auth.txt`. The API key can be obtained from the [Clash of Clans developer website](https://developer.clashofclans.com/#/). The script will extract the players from the clans and save them to the `players.xlsx` file.<br>
The script can be run using the following command:
```bash
python preprocessing.py --mode=extract --sheet_name=august --number_of_clans=2
```
where `--mode` is the mode of the script, `--sheet_name` is the name of the sheet in the `players.xlsx` file, and `--number_of_clans` is the number of clans you want to extract the players from.

After running the script, the `players.xlsx` file will be filled with the players from the clans, providing the following information:
- in-game name
- town hall level
- clan

## 2. Distributing the players into the clans
The second step is to distribute the players into the clans. This is done using the `preprocessing.py` script. The script will expect the `players.xlsx` file to be filled with the players from the clans. It will also expect the columng `team` to be filled with the index of the team (e.g. 1 for 1st team, 2 for 2nd team etc). The script will distribute the players into the clans and save them to the `players.xlsx` file.<br>
The script can be run using the following command:
```bash
python preprocessing.py --mode=distribute --sheet_name=august
```
where `--mode` is the mode of the script, `--sheet_name` is the name of the sheet in the `players.xlsx` file, and `--number_of_clans` is the number of clans you want to distribute the players into.<br>

After running the script, the team tables in `players.xlsx` file will be filled with the players distributed into their respective clans.

## 3. Calculating the final score of the players
The third step is to calculate the final score of the players. This is done using the `postprocessing.py` script. The script will expect the `players.xlsx` file to be filled with the players from the clans and distributed into the clans. The script will also expect the `clans.xlsx` file to be filled with the information about the league results and league coefficients. As of now, coefficients need to be added manually to the code. The script will calculate the final score of the players and save them to the `players.xlsx` file. <br>
The script can be run using the following command:
```bash
python postprocessing.py --sheet_name=august --number_of_teams=2
```
where `--sheet_name` is the name of the sheet in the `players.xlsx` file, and `--number_of_teams` is the number of teams you want to calculate the final score for.

After running the script, the team tables in `players.xlsx` will be filled with the final score of the players, the players will be sorted based on their final score inside of their teams. Finally, the table with all the players scores from all the teams will be created, and sorted based on the final score.<br>

This script is made with heart and soul by CROATIA & CRO ELITA 2 clans. If you have any questions or suggestions, feel free to contact me at `vedran.moskov@gmail.com` or feel free to join our discord server [here](https://discord.gg/7WnvZrAV).<br>
