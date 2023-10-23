Only need to run the file AutomateExtractingDATA.mlx, then it will execute all steps sequently.

Files' descriptions:
1. fuelmix***1: Group DUID of power plants by fueltype: Coal, Gas, Distillate, etc. for each region
2. dispatchload***1: Group DUID of power plants by load type: Battery load, PHS pump
3. separateSCADA: 
	a. separate SCADA data from AEMO by fuel mix as said in 1 and save as scadaYYYYMM.mat
	b. separate SCADA data from AEMO by load type as said in 2 and save as scada_loadYYYYMM.mat
4. funcGENMIX: called in 3.a.
5. funcDPLOAD: called in 3.b.
6. GetCombinedTable: combine all preprocessed data in the same monthly data table, save as CombinedTableYYYYMM.mat. CombinedTable contains:
	a. Generation data coming from scadaYYYYMM
	b. Load data coming from scada_loadYYYYMM
	c. Exporting data (to other region)
	d. Price data (RRP)
7. funcMWEXPORT: extract data of the exporting MW to other region, called  in 6.c.
8. funcPrice: extract data of the price in the spot market, called in 6.d.
9. parallelsave: the files were programmed for parallel computing to reduce the execution time, they require the parallel saving functions
10. separateSHOALHAVENandTUMUT3inNSW1: NSW has 2 pumped storage plants and we want to see their performance separately, so we need to separate the PHS data in the CombinedTableYYYMM.mat by this code.
	In case of Queensland: there is only 1 pumped storage plant, so don't need to run this file.
	This file is potential to pick any DUID, separate its data from its fuelmix, and see its performance in grid (i.e., operation of a gas turbine in the system)

	