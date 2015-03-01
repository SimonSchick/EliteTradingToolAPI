# DEFINITIONS #

## Normal Commodoties ##
Id | Name
---|----------------------------
51 | Advanced Catalysers
45 | Agri-Medicines
16 | Algae
24 | Aluminium
14 | Animal Meat
35 | Animal Monitors
34 | Aquaponic Systems
80 | Atmospheric Processors
48 | Auto-Fabricators
23 | Basic Medicines
79 | Battle Weapons
30 | Bauxite
59 | Beer
47 | Bertrandite
69 | Beryllium
49 | Bioreducing Lichen
39 | Biowaste
89 | Chemical Waste
7  | Clothing
28 | Cobalt
9  | Coffee
29 | Coltan
44 | Combat Stabilisers
32 | Computer Components
6  | Consumer Technology
72 | Copper
19 | Crop Harvesters
5  | Domestic Appliances
1  | Explosives
13 | Fish
12 | Food Cartridges
61 | Fruit and Vegetables
57 | Gallite
68 | Gallium
25 | Gold
15 | Grain
52 | H.E. Suits
4  | Hydrogen Fuel
92 | Imperial Slaves
56 | Indite
66 | Indium
33 | Land Enrichment Systems
38 | Leather
58 | Lepidolite
8  | Liquor
64 | Lithium
22 | Marine Equipment
20 | Microbial Furnaces
21 | Mineral Extractors
3  | Mineral Oil
43 | Narcotics
73 | Natural Fabrics
53 | Non-Lethal Weapons
65 | Palladium
55 | Performance Enhancers
42 | Personal Armor
41 | Personal Weapons
2  | Pesticides
84 | Platinum
70 | Polymers
82 | Power Generators
46 | Progenitor Cells
54 | Reactive Armour
50 | Resonating Separators
36 | Robotics
31 | Rutile
40 | Scrap
71 | Semiconductors
63 | Silver
93 | Slaves
62 | Superconductors
74 | Synthetic Fabrics
60 | Synthetic Meat
26 | Tantalum
10 | Tea
27 | Titanium
75 | Tobacco
78 | Uraninite
67 | Uranium
83 | Water Purifiers
77 | Wine

## Allegiances ##

Id | Name
---|----------------------------
1  | Alliance
2  | Empire
3  | Federation
4  | Independent
5  | None


## Economies ##

Id | Name
---|-------------
1  | Agricultural
2  | Extraction
3  | High Tech
4  | Industrial
10 | Millitary
7  | None
5  | Refinery
6  | Service
9  | Terraforming
8  | Tourism


## Government ##

Id | Name
---|--------------
1  | Anarchy
2  | Colony
3  | Communism
11 | Confederacy
13 | Cooperative
4  | Corporate
5  | Democracy
8  | Dictatorship
7  | Feudal
10 | Imperial
6  | None
12 | Patronage
14 | Prison Colony
9  | Theocracy

## StationTypes ##
Id | Name
---|--------------
5  | Outpost

# MIXINS #

## CommodityResult ##

Type   | Name
-------|----------------------------------------
number | Buy
Supply | Demand
number | DemandAmount
number | Distance
TimeDiffString | LastUpdate
number | Sell
Supply | Supply
number | SupplyAmount


## CommodityRoute ##

Type           | Name
---------------| --------------------------
TimeDiffString | BuyLastUpdate
string         | CommodityName
string         | Destination
float          | DestinationStationDistance
number         | DestinationStationId
number         | DestinationSystemId
float          | Distance
number         | Profit
TimeDiffString | SellLastUpdate
string         | Source
number         | SourceStationDistance
number         | SourceStationId
number         | SourceSystemId

## STRING ENUMS ##

### PadSize ###

- Small
- Medium
- Large

### Supply ###

- Low
- Med
- High

## COMMON ##

### RepResult ###

Type    | Name
--------|-----
string  | Badge
string  | CommandeerName
boolean | RankUp
number  | Reputation
number  | ReputationNeeded
string  | Title

### SearchQuery ###

Type         | Name
-------------|----------------
boolean      | Allegiance
stringId     | AllegianceId
boolean      | Blackmarket
boolean      | Commodity
stringId     | CommodityId
string       | CurrentLocation
boolean      | Economy
stringId     | EconomyId
boolean      | Government
stringId     | GovernmentId
boolean      | Outfitting
PadSize      | PadSize
boolean      | Repairs
stringNumber | SearchRange
boolean      | Shipyard

### Economy ###
Type   | Name
-------|-----
number | Id
string | Name

### StationType ###
Type   | Name
-------|-----------------------
string | Icon("Outpost")
number | Id
string | Name
string | Pads
string | PrimaryType("Outpost")

### Allegiance ###

Type   | Name
-------|-----
number | Id
string | Name

### Government ###

Type   | Name
-------|-----
number | Id
string | Name

### Station ###

Type                         | Name
-----------------------------|-------------------
Allegiance                   | Allegiance
number                       | AllegianceId
float                        | DistanceFromJumpIn
Economy                      | Economy
number                       | EconomyId
string                       | EconomyString
Government                   | Government
boolean                      | HasBlackMarket
boolean                      | HasMarket
boolean                      | HasOutfitting
boolean                      | HasRepair
boolean                      | HasShipyard
number                       | Id
string                       | LastUpdatedBy
date                         | LastUpdateDate
string                       | Name
Economy                      | SecondaryEconomy
number                       | SecondaryEconomyId
string                       | Services
StationCommodities(nullable) |
StationType                  | StationType
number                       | StationTypeId
number                       | SystemId
number                       | Version

### SearchResultEntry ###

Extends CommodityResult

Type    | Name
--------|-----------
date    | LastUpdate
number  | Sell
Station | Station
System  | System
string  | SystemName

### SearchQueryResult ###



Type                                                    | Name
--------------------------------------------------------|-------------------
Query(same as search query but with SearchType added)   | 
RepResult                                               | RepResult
Array of SearchResultEntry                              | Result
string(nullable)                                        | StartingSystem

### DataListSearchQuery ###

Type           | Name
-------------- | -
stringId | CommodotyId
boolean | ExcludeOutposts
string | QueryType(StationBuys/StationSells)
stringNumber | SearchRange
string | SystemName


### Commodity ###

Type    | Name
--------| -----------------------------------
number  | DistanceFromJumpIn
number  | GalacticAveragePrice
number  | Id
string  | LastUpdatedBy
string  | Location
boolean | PermitRequired
string  | StationAllegiance
string  | StationTypeIcon("Coriolis")
string  | StationTypeName("CoriolisStarport")

### DataListSearchResult ###

Type               | Name
-------------------| -----------------------------------
Array of Commodity | CommodityList
number             | QueryType(StationSells -> 2, StationBuys -> 1)
System(nullable)   | System

### System ###
Type   | Name
-------| ------
number | Id
string | Name

### TradeFindQuery ###

Type         | Name
-------------|--------------------------
stringNumber | MaxDistanceBetweenSystems
stringNumber | MaxDistanceFromJumpIn
stringNumber | MinProfitPerTon
PadSize      | PadSize
stringNumber | SearchRange
string       | SystemName

### TradeFindSearchResult ###

Type                     | Name
-------------------------|--------------------------
Array of CommodityRoute> | List
RepResult(nullable)      | RepResult

### CalculatorQuery ###

Type         | Name
-------------|----------------------
stringNumber | Cargo
stringNumber | Cash
stringNumber | EndStationId
string       | EndSystem
stringNumber | MaxDistanceFromJumpIn
stringNumber | MinProfit
PadSize      | PadSize
stringNumber | SearchRange
stringNumber | StartStationId
string       | StartSystem

### TradeCalculatorResultEntry ###

Extends CommodityRoute & CommodityResult/LastUpdate

Type    | Name
------- | ----------------------------
string  | BuyUpdatedBy
boolean | DestinationPermitRequired
string  | DestinationStationAllegiance
number  | DestinationStationDistance
string  | DestinationStationTypeIcon
string  | DestinationStationTypeName
string  | DestinationSystemName
number  | GalacticAveragePrice
number  | Qty
string  | SellUpdateBy
string  | SourcePermitRequired
string  | SourceStationAllegiance
string  | SourceStationTypeIcon
string  | SourceStationTypeName
number  | TotalProfit


### TradeCalculatorResult ###

Type                                | Name
------------------------------------| -------
Array of TradeCalculatorResultEntry | Results
RepResult                           | RepResult

### RareTradeQuery ###
Type   | Name
------ | ---------------
string | CurrentLocation

### RareTradeResult ###

Type   | Name
------ | -------------------
string | Allegiance
float  | Distance
float  | DistanceFromJumpIn
number | Id
string | Location
number | Price
string | RareTrade

# API #

## RARE TRADE SEARCH ##

ACTION           | API-CALL                  | IN                  | OUT
-----------------|---------------------------|---------------------|----------------------
SEARCH           | /Search                   | SearchQuery         | SearchQueyResult
DATA LIST        | /DataLists                | DataListSearchQuery | DataListSearchResult
AUTOCOMPLETE     | /GetStarData?query=       | STRING              | System
FIND TRADES      | /FindTrades               | TradeFindQuery      | TradeFindSearchResult
TRADE CALCULATOR | /Calculator               | CalculatorQuery     | TradeCalculatorResult
RARE TRADES      | /RareTrades               | RareTradeQuery      | RareTradeResult