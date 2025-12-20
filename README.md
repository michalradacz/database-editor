# database-editor

JSONDB web local accessible editor in EN and CS



In English and Czech language


# Czech

## Editor databází JSONDB

Tohle je webový editor databází v JSONDB formátu s komplexními funkcemi. Je absolutně přístupný i pro uživatele s odečítačem.

* [Online verze editoru](https://mrt.site44.com/database-editor.html) funguje bez instalace jen v prohlížeči
* Stáhněte si [HTML aplikaci editoru](database-editor.html) fungující kdekoliv lokálně i offline
* [Uživatelská příručka](database-editor-docs-cs.md) s popisem všech funkcí a tipů pro užívání aplikace

Používá standardizovaný popsaný [JSONDB](jsondb-format.md) ke kterému je i [schéma](jsondb-scheme.json)

Hlavní funkce

* Vytváření a správa komplexních databází: Databáze může obsahovat více tabulek a vazby mezi nimi ve stylu nadřízený a podřízený záznam, vše je plně konfigurovatelné
* JSONDB formát jako klasický schématický JSON: Možnost načít a ukládat .JSONDB soubory a nebo kopírovat JSON do schránky a opět ho ze schránky vkládat do aplikace, aby vše bylo přenositelné a funkční i se schránkou
* Několik druhů polí a to včetně polí pro závislosti mezi záznamy (ve stejné tabulce a nebo v různých tabulkách)
* Import a export: Práce s CSV a TSV soubory pro import a export dat z tabulky
* Generování libovolného textového výstupu dle šablony z dat databáze
* Přístupné standardní uživatelské rozhraní

Podrobnosti jsou v [uživatelské příručce](database-editor-docs-cs.md)

Projekt je na [GitHubu](https://github.com/michalradacz/database-editor)

# English

## Database JSONDB editor

This is a web-based database editor for the JSONDB format with comprehensive features. It is fully accessible for screenreader users.

* [Online version of the editor](https://mrt.site44.com/database-editor.html) works without installation, directly in the browser
* Download the [HTML editor application](database-editor.html) that works locally and offline anywhere
* [User guide](database-editor-docs-en.md) with a description of all features and tips for using the application

Uses the standardized documented [JSONDB](jsondb-format.md) format with an accompanying [schema](jsondb-schema.json)

Main Features

* **Creating and managing complex databases:** A database can contain multiple tables with relationships between them in a parent-child record style, all fully configurable
* **JSONDB format as standard schematic JSON:** Ability to load and save .JSONDB files or copy JSON to clipboard and paste it back into the application, ensuring everything is portable and works with clipboard
* **Several field types** including fields for dependencies between records (within the same table or across different tables)
* **Import and export:** Work with CSV and TSV files for importing and exporting table data
* **Generate any text output** from database data using templates
* **Accessible standard user interface**

Details are in the [user guide](database-editor-docs-en.md)

The project is on [GitHub](https://github.com/michalradacz/database-editor)



