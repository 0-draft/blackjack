# Blackjack

Blackjack against a dealer that lives in GitHub Actions, played by whoever turns up. Nothing to install, and no account beyond the one you already have: every decision is an issue, and the table is this file.

<!-- BLACKJACK:START -->
<div align="center"><pre><a href="https://github.com/0-draft/blackjack#blackjack"><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/label-dealer.svg" align="top" alt="dealer"></a><a href="https://github.com/0-draft/blackjack#blackjack"><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/3S.svg" align="top" alt="three of spades"></a><a href="https://github.com/0-draft/blackjack#blackjack"><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/9C.svg" align="top" alt="nine of clubs"></a><a href="https://github.com/0-draft/blackjack#blackjack"><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/blank.svg" align="top" alt=""></a>
<a href="https://github.com/0-draft/blackjack#blackjack"><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/label-player.svg" align="top" alt="player"></a><a href="https://github.com/0-draft/blackjack#blackjack"><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/9C.svg" align="top" alt="nine of clubs"></a><a href="https://github.com/0-draft/blackjack#blackjack"><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/3C.svg" align="top" alt="three of clubs"></a><a href="https://github.com/0-draft/blackjack#blackjack"><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/JC.svg" align="top" alt="jack of clubs"></a></pre></div>

<p align="center">Hand 11: the dealer had 12, @kanywst had 22 bust, and it cost 25u. Pick a chip to deal hand 12.</p>

<div align="center"><pre><a href="https://github.com/0-draft/blackjack/issues/new?title=bj%7Cbet+1+12&body=Just+click+Submit+new+issue.+The+table+updates+in+about+30+seconds."><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/chip1.svg" align="top" alt="bet 1 unit"></a><a href="https://github.com/0-draft/blackjack/issues/new?title=bj%7Cbet+2+12&body=Just+click+Submit+new+issue.+The+table+updates+in+about+30+seconds."><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/chip2.svg" align="top" alt="bet 2 units"></a><a href="https://github.com/0-draft/blackjack/issues/new?title=bj%7Cbet+5+12&body=Just+click+Submit+new+issue.+The+table+updates+in+about+30+seconds."><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/chip5.svg" align="top" alt="bet 5 units"></a><a href="https://github.com/0-draft/blackjack/issues/new?title=bj%7Cbet+10+12&body=Just+click+Submit+new+issue.+The+table+updates+in+about+30+seconds."><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/chip10.svg" align="top" alt="bet 10 units"></a><a href="https://github.com/0-draft/blackjack/issues/new?title=bj%7Cbet+25+12&body=Just+click+Submit+new+issue.+The+table+updates+in+about+30+seconds."><img src="https://raw.githubusercontent.com/0-draft/blackjack/main/.github/cards/chip25.svg" align="top" alt="bet 25 units"></a></pre></div>

<p align="center">Beat the dealer without going over 21. A click opens a prefilled issue: submit it and the table moves in about 30 seconds.</p>

<p align="center">Shoe 1 · 4.9 decks left · out of it: 8 5 7 6 7 Q 7 8 7 8 2 2 Q T T 5 K K 7 9 3 3 J 9 · <a href="https://github.com/0-draft/blackjack/blob/main/.github/blackjack.json">all 59</a></p>

<p align="center">-3u over 11 hands · 1 player · 0u lost to mistakes</p>

<table align="center">
  <thead>
    <tr><th>Hand</th><th>Player</th><th>Dealer</th><th></th></tr>
  </thead>
  <tbody>
    <tr><td><code>11</code> <a href="https://github.com/kanywst" title="@kanywst">@kanywst</a></td><td>22 bust (9 3 J)</td><td>12 (3 9)</td><td><code>-25u</code></td></tr>
    <tr><td><code>10</code> <a href="https://github.com/kanywst" title="@kanywst">@kanywst</a></td><td>20 (T K)</td><td>22 bust (5 K 7)</td><td><code>+25u</code></td></tr>
    <tr><td><code>9</code> <a href="https://github.com/kanywst" title="@kanywst">@kanywst</a></td><td>21 (7 2 2 Q)</td><td>18 (8 T)</td><td><code>+25u</code></td></tr>
  </tbody>
</table>

<p align="center">6 decks · dealer stands on soft 17 · double after split · late surrender · blackjack pays 3 to 2 · shuffled at the 75% cut card</p>
<!-- BLACKJACK:END -->

## How to play

Pick a chip to deal a hand, then hit, stand, double, split or surrender with the buttons that appear. Each click opens an issue with the decision already written in the title — press Submit, and about 30 seconds later the table above has moved and the issue is closed with a note on what that decision was worth.

There is one table and one hand at a time, so whoever clicks next is the player. A link drawn for an earlier hand is refused rather than applied to whatever is on the table now.

- Six decks, dealt down to a cut card at 75% before the shoe is shuffled
- Every card that has come out of the shoe is listed under the table. Nothing here tells you the count; counting it is the game
- Each decision is priced from the cards actually left in the shoe, and what a mistake cost is added up per player
- Every hand is kept in [.github/blackjack-log.txt](.github/blackjack-log.txt)

## How it works

`scripts/blackjack.py` is the game: the rules, the state in [.github/blackjack.json](.github/blackjack.json), and the renderer that writes the table between the two markers above. `scripts/bjmath.py` prices each decision against the shoe. `.github/workflows/blackjack.yml` runs them whenever an issue is opened whose title starts with `bj|`, then commits the redrawn README and closes the issue.

The hole card is not in the repository: the state file is public, so the dealer's second card is not drawn until it is turned over.

The cards in `.github/cards` are drawn by `scripts/make_cards.py` and committed rather than generated on each hand, so `.github/workflows/checks.yml` regenerates them on every pull request and fails if the committed art no longer matches its generator. `.github/workflows/calculator.yml` checks the calculator against all 260 cells of the published basic-strategy chart, nightly and on any change to it.

Moved out of the [kanywst/kanywst](https://github.com/kanywst/kanywst) profile README on 2026-10-02, with the shoe and the scores as they stood.
