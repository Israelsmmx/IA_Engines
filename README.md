# IA_Engines

Testing of different IA engines like chat GPT based on the serge repo,

# ALPACA TESTING With Cluster

Git repo:
            <https://github.com/serge-chat/serge>

            Kudos for the great team that share this engine to make a test with different IAs 

            <https://github.com/serge-chat>
                       

docker immage
         
             ghcr.io/serge-chat/serge:latest

Download the repo

            git clone https://github.com/serge-chat/serge.git
                
         
## Tunnning on the WSL2 configuration

  the idea is try to assign and balance the available resources
  
  ![image](https://github.com/Israelsmmx/IA_Engines/assets/84999244/68cdb59c-d25c-42aa-a065-0928aeac96e2)


### Edit the .wslconfig to assign resources, this will prevent the system comes down or freeze the systems
        
            C:\Users\<User>\.wslconfig

### Reference values on the file, keep resources available for the system management

    ** Notes: ** if you have aditional unit use a diferent disk for swap
    
    

            # Settings apply across all Linux distros running on WSL 2
            [wsl2]
            # Limits VM memory to use no more than 4 GB, this can be set as whole numbers using GB or MB
            memory=40GB 
            # Sets the VM to use two virtual processors
            processors=24
            # Sets amount of swap storage space to 8GB, default is 25% of available RAM
            swap=30GB
            # Sets swapfile path location, default is %USERPROFILE%\AppData\Local\Temp\swap.vhdx
            swapfile=G:\\WSL\\swap\\wsl-swap.vhdx
            # Disable page reporting so WSL retains all allocated memory claimed from Windows and releases none back when free
            pageReporting=false
            # Turn off default connection to bind WSL 2 localhost to Windows localhost
            localhostforwarding=true
            # Disables nested virtualization
            nestedVirtualization=false
            # Turns on output console showing contents of dmesg when opening a WSL 2 distro for debugging
            debugConsole=false


# Run the cluster and container with compatibilty of cores and memory

    docker-compose --compatibility up


## Sample of docker-compose file    


            services:
              serge:
                image: ghcr.io/serge-chat/serge:latest
                container_name: serge
                restart: unless-stopped
                ports:
                  - 8008:8008
                volumes:
                  - weights:/usr/src/app/weights
                  - datadb:/data/db/
                deploy:
                  resources:
                    limits:
                      cpus: '20'
                      memory: 40G
                    reservations:
                      cpus: '20'
                      memory: 40G
            volumes:
                  weights:
                  datadb:

## Notes:

  spme times the engine needs a small kick with CTRL + Enter Again to request reformulate the answare

  
  ![image](https://github.com/Israelsmmx/IA_Engines/assets/84999244/96f8952b-145b-4d18-9ae2-0dfc80293a78)


  
  ![image](https://github.com/Israelsmmx/IA_Engines/assets/84999244/b819c480-79b3-4149-b0ba-33d63a0fabeb)

