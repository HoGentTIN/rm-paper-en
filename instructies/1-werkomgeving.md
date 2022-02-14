# Phase 1. Work environment setup

In this course you will make use of different software packages and tools. In this phase we will install and configure the necessary applications for an efficient work environment.

## Software Installation 

This is what you need:

- A Git client ([Git CLI](https://git-scm.com), [Gitkraken](https://git-scm.com), ...)
- A LaTeX-distribution:
    - Windows: [MikTeX](https://miktex.org) of [TeX live](https://www.tug.org/texlive/) (aanbevolen in combinatie met VS Code)
    - MacOS X: [MacTeX](https://www.tug.org/mactex/)
    - Linux: [TeX live](https://www.tug.org/texlive/))
- A LaTeX IDE or editor with LaTeX support:
    - [Texstudio](https://www.texstudio.org) is a complete IDE, specifically for LaTeX
    - [Visual Studio Code](https://code.visualstudio.com) has good support, but requires some fiddling [configuring](https://dev.to/ucscmozilla/how-to-create-and-compile-latex-documents-on-visual-studio-code-3jbk)
- [JabRef](https://www.jabref.org), a bibliografic database specifically for LaTeX
- An editor with Markdown support is also convenient
    - [Visual Studio Code](https://code.visualstudio.com) has excellent support (i.e. HTML preview with `Ctrl+Shift+V`)
    - [Typora](https://typora.io)

### Windows

We suggest to use [Chocolatey Package Manager](https://chocolatey.org/install) for the management of installed applications.

Open a Powershell or CMD terminal as Administrator and select from the commands listed below for the specific packages you'd like to install. Please notice that text behind the (`#`) symbol is not executed, hence does not need to be copied and is defined as comment!

```powershell
choco install -y git        # CLI client
choco install -y gitkraken  # Graphical Git client (optional)
choco install -y miktex     # LaTeX distribution
choco install -y texlive    # Alternatieve LaTeX distro (choose either one, but only 1!)
choco install -y texstudio  # Complete LaTeX IDE
choco install -y vscode     # Visual Studio Code (optional)
choco install -y JabRef     # Bibliographic database
choco install -y typora     # Markdown editor (optional)
```

### MacOS X

We suggest to use the [Homebrew package manager](https://brew.sh/) for the management of installed applications. *Please notice: this procedure has not been tested recently, any feedback will be appreciated!*

Open a Terminal and select from the commands below the specific packages that you would like to install. Please notice that text behind the (`#`) symbol is not executed, hence does not need to be copied and is defined as comment!

```bash
brew install git               # CLI client
brew install --cask gitkraken  # Graphical Git client (optional)
brew install --cask mactex     # LaTeX distribution
brew install --cask texstudio  # Complete LaTeX IDE
brew install --cask visual-studio-code # VS Code (optional)
brew install --cask jabref     # Bibliographic database
brew install --cask typora     # Markdown editor (optional)
```

### Linux (Debian/Ubuntu)

Linux users know that there are differences in software installation procedures, depending on the distribution. A few instructions for distributions from the Debian-family (Ubuntu, Mint, enz.). For other distributions the command and package names can differ, but mostly Linux users are aware of this.

```bash
sudo apt install git        # CLI client
sudo apt install texlive    # LaTeX distribution
sudo apt install texstudio  # Complete LaTeX IDE
sudo apt install jabref     # Bibliographic database

wget https://release.gitkraken.com/linux/gitkraken-amd64.deb
sudo dpkg -i gitkraken-amd64.deb  # Graphical Git client (optional)

# Download the .deb package first from https://code.visualstudio.com/Download
sudo dpkg -i ./code_*.deb   # VS Code
```

De **TeX live** distribution is very extensive and was divided into different packages. `texlive` is the basic installation, `texlive-full` the complete distribution (including parts you might never need). The choice is yours: either you install TeX live completely, either the basic installation complemented with the extra features you need, e.g. `texlive-science`, `texlive-xetex`, etc. For a detailed overview of availble features you can explore the `apt search texlive`. You will have to find out for yourself what you really need and what you have to install additionally.

## Configuration Git, Github

Normally, you should have already made a Github-account and personal Github repository via the Github Classroom link that you can find on the Chamilo platform.

### Basic configuration

Before you will use Git on your laptop it is important to configure some **basic settings**. If you won't, your commits will not always be pushed correctly to github in your name. Especially for group assignments, this is a problem as it is impossible to distinguish between your contributions and your fellow students'!

- Connect your **HoGent email address** to you Github account (you can register multiple addresses). This way, you can claim a [Github student developer pack](https://education.github.com/pack), allowing free access to some paying products and services.
- [Generate an SSH key pair](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) if you haven't already and [register it on Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).
- Set up your name and (HOGENT-) email. Using the CLI:

    ```console
    git config --global user.name "Pieter Stevens"
    git config --global user.email pieter.stevens.u12345@student.hogent.be
    git config --global github.user PieterStevens
    ```

- Pas [some basic settings](https://git-scm.com/book/nl/v2/Git-aanpassen-Git-configuratie) aan:

    ```bash
    git config --global push.default simple
    git config --global pull.rebase true
    git config --global rebase.autoStash true
    git config --global init.defaultBranch main
    ```

    Please go through the [documentation](https://git-scm.com/book/nl/v2/Git-aanpassen-Git-configuratie) to find out what these commands do.

- Clone your Github-repo onto your laptop.

### Recommendations

We assume that you are able to work with Git/Github! Some recommendations:

- **Avoid** using the **Github webinterface** for adding/adapting file content. Clone your repository locally onto your laptop and use the command-line or a decent GUI. 
- **Commit and push** as often as possible!
- Create [**atomic commits**](https://dev.to/cbillowes/why-i-create-atomic-commits-in-git-kfi). Your github-repository is a backup that helps you from losing your work in progress. 
- Provide a clear description for your commits in the [**commit messsage**](https://cbea.ms/git-commit/).
- The standard for formatted text on Github is [Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax). Please take your time to learn how to write a **Markdown-document** and explore its layout (in an editor or on Github).

## LaTeX

LaTeX bestaat al enkele decennia. Waar het vroeger enkel mogelijk was om in een LaTeX-document ASCII-tekst te gebruiken, is het nu volledig UTF-8 compatibel. De meeste LaTeX-gerelateerde tools hebben in hun basisinstellingen echter nog steeds die oorspronkelijke werkwijze geconfigureerd. Enkele aanpassingen zijn dus nodig!

### TeXStudio configureren

Controleer deze instellingen via menu-item *Options > Configure TeXstudio*

- Build:
    - Default Compiler: **XeLaTeX** (UTF-8 compatibel, mogelijkheid om TTF-lettertypes te gebruiken, enz.) in plaats van PDFLaTeX (enkel ASCII, PostScript lettertypes, enz.)
    - Default Bibliography tool: **`biber`** (UTF-8 compatibel, ondersteuning voor APA-referenties, ...) in plaats van `bibtex` (enkel ASCII, geep APA-referenties, ...)
- Commands:
    - XeLaTeX: `xelatex -synctex=1 -interaction=nonstopmode -shell-escape %.tex` (voeg de optie `-shell-escape` toe)
- Editor:
    - Indentation mode: *Indent and Unindent Automatically*
    - Replace Indentation Tab by Spaces: *Aanvinken*
    - Replace Tab in Text by spaces: *Aanvinken*
    - Replace Double Quotes: *English Quotes: ``''*

Om te testen of TeXStudio goed werkt, kan je het sjabloon voor de paper ( `paper/FamilienaamVoornaamJaarRM.tex`) gebruiken. Verander eerste de bestandsnaam in je eigen naam (familienaam eerst) en het jaartal (bv. `DeSmetJan2022RM.tex`).

Kies *Tools > Build & View* (of functietoets `F5`) om deze te compileren in een PDF-bestand. **Let op!** Als het resulterende PDF-bestand geen bibliografie bevat, moet je die nog apart compileren. Dit kan via het menu *Tools > Bibliography* of functietoets `F8`. Daarna doe je op nieuw *Build & View*.

Veel functionaliteiten van LaTeX zitten in aparte packages die niet noodzakelijk standaard geïnstalleerd zijn. De eerste keer dat je een bestand compileert, is het dan ook mogelijk dat er extra packages moeten gedownload worden. MiKTeX op Windows zal een pop-up tonen om je toestemming te vragen, bevestig dit. De eerste keer compileren kan enkele minuten duren zonder dat je feedback krijgt over wat er gebeurt. Even geduld, dus. Op Linux werkt dit misschien niet en moet je opzoeken welke extra packages `texlive` je nog moet installeren voor de gewenste functionaliteit.

Indien er zich fouten voordoen bij de compilatie, kan je onderaan in het tabblad *Log* een overzicht krijgen van de foutboodschappen. Wanneer je bij je lector hulp vraagt, is het belangrijk om de **exacte foutboodschap** mee te geven. Dat kan het makkelijkst door het tabblad *Logbestand* te selecteren en de gehele inhoud te kopiëren.

### Visual Studio Code

VS Code is een krachtige teksteditor met zeer goede ondersteuning voor tientallen programmeer- en scriptingtalen en gestructureerde tekstformaten als HTML, Markdown, enz. Ook voor LaTeX zijn er goede plugins. Als je al gewend bent om VS Code te gebruiken, dan kan je het even goed ook gebruiken voor LaTeX. Het nadeel is misschien wel dat het wat complexer is om Code goed te configureren, in die mate zelfs dat het ons hier te ver zou leiden om een volledig stappenplan te voorzien.

Installeer in elk geval [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) van James Yu. Pas de configuratie aan zodat de `xelatex` compiler gebruikt wordt in plaats van `pdflatex`. Lees [de documentatie](https://github.com/James-Yu/LaTeX-Workshop/wiki) voor meer info en inspireer je eventueel op [dit VS Code configuratiebestand](https://github.com/bertvv/dotfiles/blob/master/.config/Code/User/settings.json) om LaTeX Workshop in te stellen.

### JabRef

[JabRef](http://www.jabref.org/) is een GUI voor het bewerken van BibTeX-bestanden, een soort database van bronnen uit de wetenschappelijke of vakliteratuur voor een LaTeX-document. De interface en instellingen veranderen nogal eens tussen versies, dus het is mogelijk dat deze instructies niet meer exact werken.

Binnen de LaTeX-wereld is er een apart subsysteem voor het correct opmaken van een referentielijst of bibliografie. Het "oude" systeem heet BibTeX en is vaak de standaard in LaTeX-editors. Het sjabloon voor de paper en ook dat voor de bachelorproef zijn echter gebaseerd op een modernere vervanger, BibLaTeX/biber. Pas Jabref aan om standaard het laatste te gebruiken.

- Kies in het menu voor *Options > Preferences > General* en kies onderaan voor de optie "Default bibliography mode" voor "biblatex".
- Kies in het *Preferences*-venster voor de categorie *File* en geef een directory op voor het bijhouden van PDFs van de gevonden bronnen onder *Main file directory*. Het is heel interessant om de gevonden artikels te downloaden en onder die directory bij te houden. Nog beter is om als naam van het bestand de BibTeX key te nemen (typisch naam van de eerste auteur + jaartal, bv. Knuth1998.pdf). Je kan het bestand dan makkelijk openen vanuit Jabref.

## Checklist

- [ ] De nodige software is geïnstalleerd.
- [ ] De basisinstellingen van Git zijn waar nodig aangepast. Bij een commit naar Github is duidelijk wie de auteur is.
- [ ] TeXstudio of VS Code zijn geconfigureerd voor gebruik.
- [ ] Het sjabloon compileert zonder fouten, in de PDF is ook de (voorbeeld-)bibliografie opgenomen.
