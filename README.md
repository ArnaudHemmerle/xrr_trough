# XRR

Scripts and instructions for XRR on liquid-air interfaces.

## Alignment

- Send basez to -4
- Align m4 (pitch and tz) parallel with the beam and report m4pitch0 in the notebook
- Slits need to be well aligned, offset and gap (in particular ss1)

## Calibration

### Alignment of the first point
- Click on ```Calib. XRR``` in JupyLabBook
- Go to the first m4pitch point (ideally on the plateau of total reflection), for example m4pitch = -0.08 at 8 keV
- Align c10tablepitch and zs
- Tune gamma so that the reflected beam is in the desired zone of the Pilatus (for ex. y=925)
- Create a small ROI centered on the reflected beam (useful for control on Salsa)
- Report the values and the distance Pilatus-trough (center of the trough)
- Click on ```Start```

### Calibration
For each line of the table (except the first one, already done):
- Move m4pitch and zs to their suggested values
- Move c10tablepitch and gamma to their suggested values
- Adjust the attenuators
- Align gamma so that the reflection is in the center of the ROI
- Optional (it is usually very good already): align c10tablepitch around its suggested value
- Align zs around its suggested value
- Replace the values in the table

When done, execute the cell.

### Report values in the XRR scripts
- In ```XRR.ipy```, put the right values in:
    - coeff_c10tablepith
    - coeff_zs
    - coeff_gamma
    - D_pilatus
    - abs_value
    - path_folder  
    
    
- In ```XRR_cont_regh.ipy```, check that the moves are ok and put the right values in:
    - gamma_XRR
    - delta_XRR
    - abs_value  


- In ```XRR_direct.ipy```, put the right value in:
    - abs_value  

## Do a scan
- Edit ```XRR_prepare.ipy```
- **Run ```XRR_prepare.ipy```** and check that the values are ok
- Run ```XRR.ipy```

## Extract the scan using JupyLabBook

### First scan of the experiment
- Select and treat the first XRR scan (careful, not the direct)
- Fill in ROI x0/y0/sizex/sizey
- Check the result with the button ```Show ROI```. Verify that the ROI is long enough to contain all the reflected beams (if the beam moves a bit)
- Fill m4pitch0 and wavelength
- If there is no direct scan, force the value of the direct (for normalization)
- If there is a direct scan, select it. Check that the ROI is long enough to contain the direct by clicking on ```Show ROI Direct```
- No need to plot gains, but better to plot m4pitch and qz
- Click on ```Extract & Plot XRR```

### Next scans
Previous values are the default ones (no need to check everything).
- Select and treat the first XRR scan (careful, not the direct)
- Click on ```Extract & Plot XRR```

## Results
Results are saved as a text file in the working directory.  
There is a header : #m4pitch(deg)    #theta(rad)    #qz(nm-1)    #I0    #I    #direct    #R
