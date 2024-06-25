# EXAPUNKS

My solutions to the game [EXAPUNKS](https://www.zachtronics.com/exapunks/) by [Zachtronics](https://www.zachtronics.com/) in which you need to solve puzzles by writing tiny programs in an assembly-like language.

This is a fork of [starbust997's repo](https://github.com/starburst997/EXAPUNKS), which includes a solution parser for automatically generating this fancy repository along with result tables, EXA code in text format, GIFs and so on.

## Solutions

My solutions are not record-breaking, but typically average or better.

In most levels I aimed for reducing cycle count while keeping the code simple and readable. In some levels (mainly the Visual Cortex and Last Stop Warehouse) I thought it'd be more fun to go for minimal activity by using a lot of networking.

There are not a lot of comments in my code, however there is some indentation so that "functions" and some branches stand out more.

<!-- EXA_START -->
#### Levels
| Level                                                                                                                                | Cycles | Size | Activity |
|--------------------------------------------------------------------------------------------------------------------------------------|--------|------|----------|
| [1: Trash World News (Tutorial 1)](solutions/01-trash-world-news-tutorial-1) | 4      | 3    | 2        |
| [2: Trash World News (Tutorial 2)](solutions/02-trash-world-news-tutorial-2) | 9      | 9    | 2        |
| [3: Trash World News (Tutorial 3)](solutions/03-trash-world-news-tutorial-3) | 11     | 15   | 4        |
| [4: Trash World News (Tutorial 4)](solutions/04-trash-world-news-tutorial-4) | 306    | 13   | 2        |
| [5: Euclid's Pizza (Order System)](solutions/05-euclids-pizza-order-system) | 29     | 29   | 1        |
| [6: Mitsuzen HDI-10 (Left Arm)](solutions/06-mitsuzen-hdi-10-left-arm) | 184    | 24   | 5        |
| [7: Last Stop Snaxnet (Factory 11)](solutions/07-last-stop-snaxnet-factory-11) | 32     | 13   | 2        |
| [8: Zebros Copies (Point-Of-Sale System)](solutions/08-zebros-copies-point-of-sale-system) | 80     | 32   | 2        |
| [9: SFCTA Highway Sign #4902 (Remote Access Interface)](solutions/09-sfcta-highway-sign-4902-remote-access-interface) | 151    | 15   | 1        |
| [10: Unknown Network 1 (Unknown Context)](solutions/10-unknown-network-1-unknown-context) | 35     | 19   | 27       |
| [11: UC Berkeley (EECS Department)](solutions/11-uc-berkeley-eecs-department) | 128    | 48   | 7        |
| [12: Workhouse (Work Management System)](solutions/12-workhouse-work-management-system) | 344    | 58   | 2        |
| [13: Equity First Bank (San Fancisco)](solutions/13-equity-first-bank-san-fancisco) | 1461   | 36   | 10       |
| [14: Mitsuzen HDI-10 (Heart)](solutions/14-mitsuzen-hdi-10-heart) | 85     | 30   | 7        |
| [15: Trash World News (Unknown Context)](solutions/15-trash-world-news-unknown-context) | 563    | 36   | 3        |
| [16: TEC Redshift (Development Kit)](solutions/16-tec-redshift-development-kit) | 6951   | 26   | 4        |
| [17: Digital Library Project (Patron Access System)](solutions/17-digital-library-project-patron-access-system) | 307    | 32   | 74       |
| [18: TEC EXA-Blaster Modem (Radio Stations)](solutions/18-tec-exa-blaster-modem-radio-stations) | 246    | 62   | 22       |
| [19: Emerson's Guide (Streetsmarts GIS Database)](solutions/19-emersons-guide-streetsmarts-gis-database) | 52     | 40   | 6        |
| [20: Mitsuzen HDI-10 (Left Hand)](solutions/20-mitsuzen-hdi-10-left-hand) | 99     | 38   | 263      |
| [21: Sawayama Wonderdisc (Drive Controller)](solutions/21-sawayama-wonderdisc-drive-controller) | 8291   | 54   | 63       |
| [22: Alliance Power and Light (Streetsmarts GIS Database)](solutions/22-alliance-power-and-light-streetsmarts-gis-database) | 37     | 31   | 40       |
| [23: Xtreme League Baseball (Player Database)](solutions/23-xtreme-league-baseball-player-database) | 308    | 53   | 1        |
| [24: King's Ransom Online (US West Realm)](solutions/24-kings-ransom-online-us-west-realm) | 41     | 36   | 25       |
| [25: KGOG-TV (Satellite Uplink)](solutions/25-kgog-tv-satellite-uplink) | 375    | 89   | 8        |
| [26: Equity First Bank (San Francisco - ATMs Offline)](solutions/26-equity-first-bank-san-francisco-atms-offline) | 142    | 49   | 2        |
| [27: TEC EXA-Blaster Modem (Dataphone Network)](solutions/27-tec-exa-blaster-modem-dataphone-network) | 1355   | 67   | 9        |
| [28: Last Stop Snaxnet (Warehouse 27)](solutions/28-last-stop-snaxnet-warehouse-27) | 177    | 92   | 7        |
| [29: Mitsuzen HDI-10 (Visual Cortex)](solutions/29-mitsuzen-hdi-10-visual-cortex) | 1498   | 56   | 10       |
| [30: Holman Dynamics (Sales System)](solutions/30-holman-dynamics-sales-system) | 5619   | 130  | 3        |
| [31: US Government (Fema Genetic Database)](solutions/31-us-government-fema-genetic-database) | 809    | 126  | 45       |
| [32: Unknown Network 2 (Unknown Context)](solutions/32-unknown-network-2-unknown-context) | 108    | 74   | 53       |
| [33: TEC EXA-Blaster Modem (Pager Network)](solutions/33-tec-exa-blaster-modem-pager-network) | 805    | 52   | 9        |
| [34: Mitsuzen HDI-10 (Cerebral Cortex)](solutions/34-mitsuzen-hdi-10-cerebral-cortex) | 1619   | 141  | 89       |
#### Battles
 * [1: KGOG-TV (Programming Hub)](battles/01-kgog-tv-programming-hub)
 * [2: Valhalla (=Plastered)](battles/02-valhalla-plastered)
 * [3: Deadlock's Domain (Deadlock)](battles/03-deadlocks-domain-deadlock)
 * [4: The Wormhole (X10X10X)](battles/04-the-wormhole-x10x10x)
 * [5: Aberdeen (selenium_wolf)](battles/05-aberdeen-seleniumwolf)
#### Bonus

| Bonus campaign level                                                                                                                                | Cycles | Size | Activity |
|--------------------------------------------------------------------------------------------------------------------------------------|--------|------|----------|
| 1: Bloodlust Online (US East Realm) | N/A | N/A | N/A |
| 2: Motor Vehicle Administration (Scheduling System) | N/A | N/A | N/A |
| 3: Cybermyth Studios (Accounting System) | N/A | N/A | N/A |
| 4: US Department of Defense (USAF Secure Facility) | N/A | N/A | N/A |
| 5: Netronics NET40 Modem (The Wardialer) | N/A | N/A | N/A |
| 6: Española Valley High School (School Management System) | N/A | N/A | N/A |
| 7: Mitsuzen D300-N (Personal Storage Array) | N/A | N/A | N/A |
| 8: Crystalair International (Ticketing System) | N/A | N/A | N/A |
| 9: Your Computer (Unknown Context) | N/A | N/A | N/A |
<!-- EXA_END -->

## TODO
 [ ] Bonuses
 [ ] Sort out the battles
