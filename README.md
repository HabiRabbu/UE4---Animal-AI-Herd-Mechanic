# Sheep AI in Game: Realism Enhancement
Welcome to the Sheep AI project, an endeavour aimed at enhancing the realism of sheep behaviour in a gaming environment. Here's a breakdown of the project, its behaviours, and some insights into its implementation:

## Background:
Sheep are social creatures that usually graze together for security. Predominantly, their activities revolve around either grazing, which is a mix of eating and waiting (termed "Graze/Wait"), exploring their surroundings ("Roam"), or running away when they perceive danger ("Run away"). Emulating these behaviours in an AI-driven game environment not only makes them more lifelike but also enriches the overall player experience.

## Behavior Implementation:
1. Graze/Wait State:
Here, the sheep are in a passive mode, constantly in wait for a possible player collision with its surrounding sphere.
During this state, the sheep is also prepared for the "roam around" event unless there's an ongoing player-sphere collision.
2. Roam State:
This event is scheduled to run continuously but with a delay.
If the roam event becomes dominant over the graze/wait state, the sheep is set in motion to a random location within the navigation mesh terrain.
Once arrived, the sheep faces the appropriate direction and an associated sound is played.
3. Run Away State:
This state is triggered conditionally based on the player's proximity to the sheep, as determined by the sheep’s sphere.
If the player enters this sphere, the AI checks if the player is crouching via the isCrouching boolean (CTRL to toggle).
In cases where the player is crouching, the sheep remains passive and doesn't transition to the "Run Away" state.
However, if the player isn't in a crouched posture, the sheep, sensing potential danger, faces the direction opposite to the player and scurries to a safer distance.
Once the perceived threat has passed, the sheep reverts to its initial behaviour of grazing or roaming.
