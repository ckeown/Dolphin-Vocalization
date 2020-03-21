# Dolphin-Vocalization
DolphinVocalization

## Time/location processing.
`ALL_FinalCrossing - Sheet1.csv` is derived from the original Google sheet Chris gave us.  It was processed 
to include boolean columns for all gates indicating when they are closed.

`03.DolphinLocationProcessing` transforms ALL_FinalCrossing into `processed_dolphin_locations.csv`.  Column titles should be self-explanatory.  Note that feeding times can result in a dolphin having no position and in a list of '0' values in the tank _contains fields.

**Important**

Please using the following code to read the locations file as a pandas data frame -- the transformation to/from csv has some gotchas.


    import pandas as pd

    contains_converters = {c: eval for c in ['DD_contains',
                                             'G1_contains',
                                             'G2_contains',
                                             'G3_contains',
                                             'G4_contains',
                                             'MN_contains',
                                             'NH_contains',
                                             'SH_contains']}

    dolphin_locations = pd.read_csv('processed_dolphin_locations.csv', index_col=0,
                                    converters=contains_converters)
    
    dolphin_locations.fillna('', inplace=True)

