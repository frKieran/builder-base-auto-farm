# builder-base-auto-farm
Python utility that helps you farm resources in the Builder Base across multiple accounts seamlessly.
## Requirements
### Operating System:
- [Windows 11](https://www.microsoft.com/software-download/windows11)/[10](https://www.microsoft.com/en-us/software-download/windows10)

### Software:
- [Python 3.10 or higher](https://www.python.org/downloads/) (required)
- [Google Play Games beta](https://play.google.com/googleplaygames) (required)
- [ShareX](https://getsharex.com/downloads) (optional) _(Not needed after setup, gets X and Y coordinates for pixels on the screen.)_
- [Notepad++](https://notepad-plus-plus.org/downloads/) (optional) _(Text editor for easier editing of .ini files.)_

## Dead-Simple Steps:

1. **Install Python 3.10 or higher.**
2. **Install the Google Play Games beta.**
3. **Install and run Clash of Clans, then log into the accounts you plan on using with the script.**
4. **Run  `...\resources\scripts\setup.py` via the command prompt.**
5. **Edit the placeholders in `settings.ini`** _(see deatiled information for explanations)_
6. **Modify the placeholder profile in `...\profiles`** _(see detailed information for explanations)_
7. **Rename the file to the Clash of Clans username it corresponds to.**
8. **Run `auto-farm.py` via the command prompt.**

---

## Detailed Information

### How do I use the command prompt? (Step 4)
- Press Win+R and type "cmd" to run the command prompt.
- Type `cd "directory name"` to enter a folder.
- Type `cd..` to go back a folder.
- Type `python file_name_here.py` to run a Python script via the command prompt.

The exact directory depends on where you downloaded the program. For example, it could be `C:\Users\Admin\Downloads\builder-base-auto-farm\resources\scripts\setup.py`. Check beforehand in the file explorer.

---

### Settings.ini file structure and explanations (Step 5)
Navigate to the `settings.ini` file located in the main directory and edit the placeholders with the appropriate values. Below is an explanation of each option along with their possible values.

#### [Profile]
  - **profile**: Choose the profile to use. Must be the same as the file name. Alphanumerical characters only.
    - *Example value*: `Kieran`
  - **queue**: Specify profiles to queue in a comma-separated format. Set to "False" to disable queuing.
    - *Example value*: `Kieran, John, Doe` or `False`
  - **multiple_accounts_saved**: Specifies if you have multiple accounts saved in-game via Supercell ID.
    - *Possible values*: `True`, `False`

#### [Game]
  - **fullscreen**: Specifies whether to run the game in fullscreen mode.
    - *Possible values*: `True`, `False`
  - **resolution**: Specifies the game content resolution.
    - *Example value*: `1588x893`
  - **position**: Specifies the top-left pixel coordinates of the game content.
    - *Example value*: `2, 32`

  **Note**: The game window uses a set of locked resolutions, which appear to be random. I'd recommed using ShareX to  find what resolution works the best for you. **The example coordinates and positions are optimized for a 1920x1080 screen size.** Opening the game, pressing PrintScr, and hovering over the game window shows you the size of its contents (W and H), and the top-left pixel position. (X and Y)
  
#### [Console]
  - **console_debug_logs**: Enable/disables debug logs.
    - *Possible values*: `True`, `False`
  - **console_resolution**: Specifies the console resolution.
    - *Example value*: `316x976`
  - **console_position**: Sets the position of the console.
    - *Example value*: `1602, 43`

#### [Webhook]
  - **logs_webhook**: Enable/disables logs webhook.
    - *Possible values*: `True`, `False`
  - **logs_webhook_link**: Specifies logs webhook link for Discord. This includes information about the time between attacks, the current attack number, and the loot type being farmed.
    - *Example value*: `https://discord.com/api/webhooks/server_id/webhook_id`
  - **debug_webhook**: Enable/disables debug webhook.
    - *Possible values*: `True`, `False`
- **debug_webhook_link**: Specifies a debug webhook link for Discord. Not recommended, it can clog up a channel very easily.
  - *Example value*: `https://discord.com/api/webhooks/server_id/webhook_id`

#### [Internal]
  - **skip_setup**: Do not edit this manually.

---

### Profile.ini file structure and explanations (Steps 6 & 7)
Make sure you rename this file to match the username of the Clash of Clans account it corresponds to. You can copy and paste this file to manage multiple accounts efficiently.

#### [General]
- **builder_hall_level**: Specifies the Builder Hall level.
  - *Possible values*: `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `10`
- **upgrade_walls**: When this is True, loot will be spent on walls upon storages being complete, rather than just ending the script. This can run for dozens of hours, so if you only want to fill your storages; I'd recommend leaving it False.
  - *Possible values*: `True`, `False`
- **main_base_slot**: Specifies the main base slot.
  - *Possible values*: `1`, `2`, `3`
- **account_switcher_y_position**: Specifies the Y position of the profile in the profile switcher. Again, ShareX is an easy way to get this number. Note that this doesn't work if the account needs to be scrolled to be clicked on, which is a planned feature.
  - *Example value*: `460`

#### [Resource Collection]
- **gold_storage_capacity**: Sets the capacity of gold storage.
  - *Example value*: `6500000`
- **elixir_storage_capacity**: Sets the capacity of elixir storage.
  - *Example value*: `6500000`
- **continue_at_max_storages**: Continues farming even when storages are at maximum capacity.
  - *Possible values*: `True`, `False`
- **farming_order**: Specifies the order of resource farming. "Gold, Elixir" is faster, however "Elixir, Gold" mitigates trophy loss. It's important to note that elixir is farmed alongside gold whenever "skip_elixir_cart" is False. If its set to only Gold or Elixir, it will simply farm only that resource type until completion, which is not recommended.
  - *Possible values*: `Gold, Elixir`, `Elixir, Gold`, `Gold`, `Elixir`
- **skip_elixir_cart_collection**: Skips checking for and collecting from the elixir cart.
  - *Possible values*: `True`, `False`
- **fill_elixir_cart_storage**: Fills up the elixir cart's storage after main storage is filled.
  - *Possible values*: `True`, `False`

#### [Attacking]
- **hero_available**: Specifies whether or not you have a hero available.
  - *Possible values*: `True`, `False`
- **hero_ability_available**: Specifies whether or not your hero's ability is available.
  - *Possible values*: `True`, `False`
- **hero_ability_activation_level**: Specifies what level the hero ability should activate on.
  - *Possible values*: `1`, `2`, `3`
- **hero_edge_case**: Most people can just keep this to False. It only matters if `hero_ability_available` is True and your second stage hero does not have its ability unlocked.
  - *Possible values*: `True`, `False`
- **troop_type**: Specifies troop type. A passive troop does not have an activatable ability, whereas an active troop does.
  - *Possible values*: `active`, `passive`
- **troop_slots_stage_1**: Number of troop slots you have in the first stage.
  - *Example value*: `6`
- **troop_slots_stage_2**: Number of troop slots you have in the second stage.
  - *Example value*: `8`
- **two_stage_attacks**: Enables or disables two-stage attacks. This is considerably slower than the regular method of force-quitting after deploying troops. However, it has the benefit of automatically using the hero's ability during the attack, making it useful for trophy-pushing. There's no reason to have this enabled if you frequently go against Builder Halls lower than level 6.
  - *Possible values*: `True`, `False`
- **force_quit_stage_2**: Force quits the game on the 2nd stage to save some time.
  - *Possible values*: `True`, `False`
- **cancel_search_seconds**: Sets the time to wait before resetting the matchmaking.
  - *Example value*: `10`
- **shield_protections**: When this is enabled, restarting the game will be avoided at all costs to prevent your main village from getting attacked. This is a slim possibility considering the small amount you're offline when restarting the game, but still possible nonetheless. Note this is considerably slower than normal, and does not prevent against restarts due to script errors.
  - *Possible values*: `True`, `False`
