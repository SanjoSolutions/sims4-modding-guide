## Recommended Tools

### Python

Python is required to compile the Python scripts, in case your mod includes any.

It's recommended to install the same Python version as is used by Sims 4. At the time of writing this seems to be 3.7. This can be found out by checking the info on the file `<PATH_TO_SIMS_4>/Game/Bin/python*_x64.dll`.

This can be done with [Anaconda](https://www.anaconda.com/download/success). After having installed Anaconda, create a new environment for Sims 4 by opening the `Anaconda Prompt` (you can find that under programs in Windows), and running the command `conda create --name Sims4 python=3.7`. To run Python scripts in this environment, open the `Anaconda Prompt` and switch to the environment with `conda activate Sims4`.

### Other

- [Git](https://www.git-scm.com/): For downloading code repository, versioning code and the Git Bash shell.
- [Visual Studio Code](https://code.visualstudio.com/): Free IDE that supports Python. The following extensions are recommended to be installed in Visual Studio Code:
  - [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) for Python support.
  - [XML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-xml) for increased XML support, including formatting.
  - [Sims 4 Toolkit in VS Code](https://vscode.sims4toolkit.com/): Can create the `.package` file for your mod.
  - [Clipboard History](https://marketplace.visualstudio.com/items?itemName=Anjali.clipboard-history) for a clipboard history in Visual Studio Code.
- [Sims 4 Mod Development Tools](https://github.com/SanjoSolutions/sims4-mod-development-tools): Can create the `.ts4scripts` file for your mod.
- [Sims 4 Tuning Builder](https://tdesc.lot51.cc/): This tool works well for creating and modifying tunings. The graphical user interface provides a nice way to see what options are available, including documentation for them (in many cases).
- [Sims 4 Studio](https://sims4studio.com/board/6/download-sims-studio-open-version): Good tool for opening `.package` files and extracting all files from a `.package` file via `Batch export`.

## Project template

[Project template](https://github.com/SanjoSolutions/sims4-mod-project-template)

## Other resources

- [Lot 51 - Learn to mod](https://lot51.cc/resources)
- [Python 3.7 documentation](https://docs.python.org/3.7/)

## How modding works for Sims 4

Many things can be done with XML configuration files. With those you can declare different types of objects that are added to the game system.

Some more advanced things require writing Python scripts.

## How to do things

### Adding an interaction to an object

- Add an interaction tuning to your package. Usually a [SuperInteraction](https://tdesc.lot51.cc/Interactions/Descriptions/SuperInteraction.tdesc)
- In case you'd like to put the interaction in a new category: Add a [PieMenuCategory](https://tdesc.lot51.cc/PieMenuCategories/Descriptions/PieMenuCategory.tdesc) for the category. This type comes also additionally with a SimData file.

It's also required to add the interaction to the object. A practical way to do this is to use the [Lot 51 Core Library](https://lot51.cc/core).
Here's an example for how to add an interaction to computers with it:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- S4TK Group: 00000000 -->
<I c="TuningInjector" i="snippet" m="lot51_core.snippets.injector" n="Name:snippet_Mod_Injections" s="16649738726568134617">
    <T n="mod_name">Mod Name</T>
    <T n="creator_name">Name</T>
    <L n="inject_by_object_tags">
        <U>
            <L n="tags">
                <E>Interaction_Computer</E>
                <E>Func_Computer</E>
                <E>BuyCatEE_Computer</E>
            </L>
            <L n="affordances">
                <T>123456789<-- The ID of the interaction --></T>
            </L>
        </U>
    </L>
</I>
```

Just add such tuning to your package. The [Sims 4 Tuning Builder](https://tdesc.lot51.cc/) also supports the tuning types of the Lot 51 Core Library.
