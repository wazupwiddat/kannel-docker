# kannel-docker
This will create a container with Kannel running, brearerbox, smsbox, and smppsim

## Setup Storm
 * Clone this git project
 * Run "./rebuild.sh"
 * Run "fig up -d"
 
## Configuration
 * Edit kannel/kannel.conf and update the host ip with your docker host ip

## Validating running instances
 * fig ps
 * fig logs
 
## Stopping running instances
 * fig stop
 * fig kill
 * fig rm (to remove containers)
