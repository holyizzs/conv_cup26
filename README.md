Ek Samosa Do Chai: Conv-Cup '26 bot

Tabular Q-learning agent, built on the provided submission kit.

State/action interface: each iteration the bot receives the observation (own, opponent and ball positions, possession, ball velocity and remaining kick distance, obstacles, attack direction). It reduces this to a 13-feature bucketed state key (positions, direction and distance to ball and opponent, possession, nearest obstacle) and looks up Q-values. It returns one action: a move (8 directions or STAY), plus a kick (direction and power 1-3) only when in possession.

Training: simulator only, on tens of thousands of randomized layouts, against the organizer bot, scripted opponents and self-play. Actions are stored in an "attack-up" frame so both sides share one table.

Safety: unseen states use a hand-written tactical fallback, and moves into walls or obstacles are filtered out.

Run: python -m team_bot.bot --model team_bot/models/trained_policy.json. No external dependencies or APIs. Randomness is seeded per match, so play is reproducible.
