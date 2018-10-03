# Installing Armbian on odroid HC1 #

 1. Get image from: https://www.armbian.com/odroid-hc1/

	Quote: *This board is stripped Odroid XU4 and we use the same
	images, however, we provide a specially optimized config (for
	kernel 4.14.y or higher) which has to be applied manually. This
	results in shorter boot time and lower consumption. Run
	armbian-config utility and go to section system -> DTB and select
	optimized board configuration for Odroid HC1. The same config is
	valid for HC2 and MC1.*
	
	    $ sha256sum Armbian_5.59_Odroidxu4_Debian_stretch_next_4.14.66.7z 
		8f915bd2c8f8af3f0c9ea4f1858b335c0d31ac99bd80ab7495fe9b256b2546b9  Armbian_5.59_Odroidxu4_Debian_stretch_next_4.14.66.7z
		$ 7zr x Armbian_5.59_Odroidxu4_Debian_stretch_next_4.14.66.7z
 
 2. Write image to sd card
 
		$ sudo su
		# dd bs=4M if=Armbian_5.59_Odroidxu4_Debian_stretch_next_4.14.66.img of=/dev/sdb conv=fsync & pid=$!
        # while kill -USR1 $pid; do sleep 1; done
		# exit
		
 3. Connect ethernet, power up, and wait for boot.
 
 4. ssh in a create user (user: `root`, password: `1234`), and reconnect with new user.
 
		$ ssh root@odroidxu4
		# exit
		$ ssh NEWUSER@odroidxu4
		
 5. Enable optimisation as per download page quote:
 
		$ sudo armbian-config
	
	Go to `system -> DTB -> hc1`, reboot and reconnect.
	
		
	
 
        
		
 
		
