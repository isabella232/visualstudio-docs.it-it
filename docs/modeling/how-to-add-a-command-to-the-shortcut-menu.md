---
title: 'Procedura: Aggiungere un comando al menu di scelta rapida'
description: Informazioni su come aggiungere comandi di menu al linguaggio specifico di dominio (DSL) in modo che gli utenti possano eseguire attività specifiche del linguaggio DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b578c949b3b5121eb90b2c034766ea15ae6d096
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386566"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Procedura: Aggiungere un comando al menu di scelta rapida

È possibile aggiungere comandi di menu al linguaggio specifico di dominio (DSL) in modo che gli utenti possano effettuare attività specifiche per il DSL. I comandi sono visualizzati nel menu di scelta rapida quando gli utenti fanno clic con il pulsante destro del mouse sul diagramma. È possibile definire un comando in modo che venga visualizzato nel menu solo in situazioni specifiche, ad esempio solo quando l'utente fa clic su tipi specifici di elementi o su elementi con uno stato specifico.

In breve, i passaggi vengono eseguiti nel progetto DslPackage come segue:

1. [Dichiarare il comando in Commands.vsct](#VSCT)

2. [Aggiornare il numero di versione del pacchetto in Package.tt](#version). È necessario effettuare questa operazione ogni volta che si modifica Commands.vsct

3. [Scrivere metodi nella classe CommandSet per](#CommandSet) rendere visibile il comando e definire le operazioni che il comando deve eseguire.

> [!NOTE]
> È inoltre possibile modificare il comportamento di alcuni comandi esistenti quali Taglia, Incolla, Seleziona tutto e Stampa eseguendo l'override dei metodi in CommandSet.cs. Per altre informazioni, vedere [Procedura: Modificare un comando di menu standard.](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

## <a name="define-a-command-using-mef"></a>Definire un comando usando MEF

Managed Extension Framework (MEF) fornisce un metodo alternativo per la definizione dei comandi di menu nel menu del diagramma. Il suo scopo principale è di consentire l'estensione di un DSL da parte dell'utente. Gli utenti possono scegliere di installare solo il DSL oppure sia il DSL sia le estensioni. Tuttavia, MEF riduce anche l'attività necessaria per definire i comandi del menu di scelta rapida, dopo l'attività iniziale di abilitazione di MEF sul DSL.

Usare il metodo descritto in questo argomento se:

1. Si vuole definire comandi di menu in menu diversi da quello di scelta rapida visualizzato facendo clic con il pulsante destro del mouse.

2. Si vuole definire raggruppamenti specifici di comandi nel menu.

3. Non si vuole consentire a terzi di estendere il DSL con comandi personalizzati.

4. Si vuole definire un solo comando.

   In alternativa, valutare la possibilità di usare il metodo MEF per definire i comandi. Per altre informazioni, vedere [Estendere il DSL usando MEF.](../modeling/extend-your-dsl-by-using-mef.md)

## <a name="declare-the-command-in-commandsvsct"></a><a name="VSCT"></a> Dichiarare il comando in Commands.Vsct
 I comandi di menu vengono dichiarati in DslPackage\Commands.vsct. Queste definizioni specificano le etichette delle voci di menu dove vengono visualizzate nei menu.

 Il file modificato, Commands.vsct, importa le definizioni da diversi file con estensione h, che si trovano nella directory *Visual Studio SDK percorso* di installazione \VisualStudioIntegration\Common\Inc. Include anche GeneratedVsct.vsct, generato dalla definizione DSL.

 Per altre informazioni sui file con estensione vsct, vedere Visual Studio [command table (. Vsct) File](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

### <a name="to-add-the-command"></a>Per aggiungere il comando

1. In **Esplora soluzioni**, nel **progetto DslPackage** aprire Commands.vsct.

2. Nell'elemento `Commands` definire uno o più pulsanti e un gruppo. Un *pulsante* è una voce del menu. Un *gruppo* è una sezione del menu. Per definire queste voci, aggiungere gli elementi seguenti:

    ```xml
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    > Ciascun pulsante o gruppo è identificato da un GUID e dall'ID di un numero intero. È possibile creare diversi gruppi e pulsanti con lo stesso GUID. Tuttavia, devono avere ID diversi. I nomi GUID e ID vengono convertiti in GUID e ID numerici effettivi nel `<Symbols>` nodo.

3. Aggiungere un vincolo di visibilità per il comando in modo che venga caricato solo nel contesto del linguaggio specifico di dominio. Per altre informazioni, vedere [Elemento VisibilityConstraints.](../extensibility/visibilityconstraints-element.md)

     Per eseguire questa operazione, aggiungere gli elementi seguenti all'elemento `CommandTable` dopo l'elemento `Commands`.

    ```xml
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. Definire i nomi usati per i GUID e gli ID. Per eseguire questa operazione, aggiungere un elemento `Symbols` all'elemento `CommandTable` dopo l'elemento `Commands`.

    ```xml
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5. Sostituire `{000...000}` con un GUID che identifica i gruppi e le voci di menu. Per ottenere un nuovo GUID, usare **lo strumento Crea GUID** nel menu Strumenti. 

    > [!NOTE]
    > Se si aggiungono altri gruppi o altre voci di menu, è possibile usare lo stesso GUID. Tuttavia, è necessario usare nuovi valori per `IDSymbols`.

6. Nel codice copiato da questa procedura, sostituire ogni occorrenza delle stringhe seguenti con le proprie stringhe:

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="update-the-package-version-in-packagett"></a><a name="version"></a> Aggiornare la versione del pacchetto in Package.tt
 Ogni volta che si aggiunge o si modifica un comando, aggiornare il parametro `version` della classe <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> applicata alla classe del pacchetto prima di rilasciare la nuova versione del linguaggio specifico di dominio.

 Poiché la classe del pacchetto è definita in un file generato, aggiornare l'attributo nel file del modello di testo che genera il file Package.cs.

### <a name="to-update-the-packagett-file"></a>Per aggiornare il file Package.tt

1. In **Esplora soluzioni**, nel **progetto DslPackage,** nella cartella **GeneratedCode** aprire il file Package.tt.

2. Trovare l'attributo `ProvideMenuResource`.

3. Incrementare il parametro della `version` dell'attributo, che è il secondo parametro. Se si vuole, è possibile scrivere il nome del parametro in modo esplicito come promemoria del suo scopo. Ad esempio:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="define-the-behavior-of-the-command"></a><a name="CommandSet"></a> Definire il comportamento del comando

Il DSL ha già alcuni comandi implementati in una classe parziale che è dichiarata in DslPackage\GeneratedCode\CommandSet.cs. Per aggiungere nuovi comandi è necessario estendere questa classe creando un nuovo file che contiene una dichiarazione parziale della stessa classe. Il nome della classe è in genere *\<YourDslName>* `CommandSet` . È utile iniziare verificando il nome della classe ed esaminando il relativo contenuto.

La classe del set di comandi è derivata da <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

### <a name="extend-the-commandset-class"></a>Estendere la classe CommandSet

1. In Esplora soluzioni, nel progetto DslPackage aprire la cartella GeneratedCode, cercare in CommandSet.tt e aprire il file CommandSet.cs generato. Prendere nota dello spazio dei nomi e del nome della prima classe definita qui. Può, ad esempio, essere visualizzato:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. In **DslPackage** creare una cartella denominata **Codice personalizzato**. In questa cartella creare un nuovo file di classe denominato `CommandSet.cs` .

3. Nel nuovo file scrivere una dichiarazione parziale con lo stesso spazio dei nomi e lo stesso nome della classe parziale generata. Ad esempio:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     > [!NOTE]
     > Se è stato usato il modello di classe per creare il nuovo file, è necessario correggere sia lo spazio dei nomi che il nome della classe.

Il codice del set di comandi deve in genere importare gli spazi dei nomi seguenti:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

Modificare lo spazio dei nomi e il nome della classe in modo che corrispondano a quelli del file CommandSet.cs generato:

```csharp
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

È necessario definire due metodi, uno per determinare quando il comando sarà visibile nel menu di scelta rapida e l'altro per eseguire il comando. Questi metodi non sono override, ma vengono registrati in un elenco di comandi.

### <a name="define-when-the-command-will-be-visible"></a>Definire quando sarà visibile il comando
 Per ogni comando, definire un metodo che determina se il comando verrà visualizzato nel menu e se verrà abilitato `OnStatus...` o disattivata. Impostare le `Visible` proprietà e di , come illustrato `Enabled` `MenuCommand` nell'esempio seguente. Questo metodo è chiamato allo scopo di costruire il menu di scelta rapida ogni volta che l'utente fa clic con il pulsante destro del mouse sul diagramma, quindi deve funzionare rapidamente.

 In questo esempio il comando è visibile solo quando l'utente ha scelto un tipo specifico di forma ed è abilitato solo quando almeno uno degli elementi selezionati si trova in uno stato specifico. L'esempio è basato sul modello DSL del diagramma classi, e ClassShape e ModelClass sono tipi definiti nel DSL:

```csharp
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

I frammenti seguenti sono spesso utili nei metodi OnStatus:

- `this.CurrentSelection`. La forma su cui l'utente ha fatto clic con il pulsante destro del mouse è sempre inclusa in questo elenco. Se l'utente fa clic su una parte vuota del diagramma, il diagramma è l'unico membro dell'elenco.

- `this.IsDiagramSelected()` - `true` se l'utente ha fatto clic su una parte vuota del diagramma.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` - L'utente non ha selezionato più oggetti

- `this.SingleSelection` : forma o diagramma su cui l'utente ha fatto clic con il pulsante destro del mouse

- `shape.ModelElement as MyLanguageElement` : elemento del modello rappresentato da una forma.

Come linea guida generale, creare una dipendenza tra la proprietà `Visible` e il contenuto selezionato e creare una dipendenza tra la proprietà `Enabled` e lo stato degli elementi selezionati.

Un metodo OnStatus non deve modificare lo stato dello store.

### <a name="define-what-the-command-does"></a>Definire l'azione del comando
 Per ogni comando, definire un metodo `OnMenu...` che esegua l'azione richiesta quando l'utente fa clic sul comando di menu.

 Se si apportano modifiche agli elementi del modello, è necessario effettuare questa operazione all'interno di una transazione. Per altre informazioni, vedere [Procedura: Modificare un comando di menu standard.](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

 In questo esempio, `ClassShape`, `ModelClass` e `Comment` sono tipi definiti nel DSL, che è derivato dal modello DSL del diagramma classi.

```csharp
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 Per altre informazioni su come spostarsi da un oggetto all'altro nel modello e su come creare oggetti e collegamenti, vedere Procedura: Modificare un comando [di menu standard.](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

### <a name="register-the-command"></a>Registrare il comando
 Ripetere in C# le dichiarazioni dei valori GUID e id effettuate nella sezione Symbols di CommandSet.vsct:

```csharp
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Usare lo stesso valore GUID inserito in **Commands.vsct.**

> [!NOTE]
> Se si modifica la sezione Symbols del file VSCT, è necessario anche modificare queste dichiarazioni in modo corrispondente e incrementare il numero di versione in Package.tt.

 Registrare i comandi di menu come parte di questo set di comandi. `GetMenuCommands()` viene chiamato una volta quando viene inizializzato il diagramma:

```csharp
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>Testare il comando
 Creare ed eseguire il DSL in un'istanza sperimentale di Visual Studio. Il comando viene visualizzato nel menu di scelta rapida nelle situazioni specificate.

### <a name="to-exercise-the-command"></a>Per verificare il comando

1. Sulla barra **degli Esplora soluzioni** fare clic su Trasforma tutti **i modelli**.

2. Premere **F5 per** ricompilare la soluzione e avviare il debug del linguaggio specifico di dominio nella compilazione sperimentale.

3. Nella build sperimentale aprire un diagramma di esempio.

4. Fare clic con il pulsante destro del mouse nel diagramma per verificare che il comando sia abilitato o disabilitato correttamente e visualizzato o nascosto in modo appropriato, a seconda dell'elemento selezionato.

## <a name="troubleshoot"></a>Risolvere problemi

**Il comando non viene visualizzato nel menu:**

- Il comando viene visualizzato solo nelle istanze di debug di Visual Studio, fino a quando si installa il pacchetto DSL. Per altre informazioni, vedere [Distribuzione di soluzioni per un linguaggio specifico di dominio](msi-and-vsix-deployment-of-a-dsl.md).

- Assicurarsi che il codice di esempio sperimentale presenti l'estensione del nome file corretto per il DSL. Per controllare l'estensione del nome file, aprire DslDefinition.dsl nell'istanza principale di Visual Studio. In Esplora DSL, fare clic con il pulsante destro del mouse sul nodo Editor, quindi fare clic su Proprietà. Nella finestra Proprietà esaminare la proprietà FileExtension.

- Il numero [di versione del pacchetto è stato incrementato?](#version)

- Impostare un punto di interruzione all'inizio del metodo OnStatus. L'interruzione dovrebbe avvenire quando si fa clic con il pulsante destro del mouse su qualsiasi parte del diagramma.

**Il metodo OnStatus non viene chiamato:**

- Assicurarsi che i GUID e gli ID del codice CommandSet corrispondano a quelli della sezione Symbols di Commands.vsct.

- In Commands.vsct verificare che il GUID e l'ID di ogni nodo padre identifichino il gruppo padre corretto.

- In un prompt dei comandi di Visual Studio digitare devenv /rootsuffix exp /setup, quindi riavviare l'istanza di debug di Visual Studio.

- Eseguire il metodo OnStatus per verificare che command.Visible e command.Enabled siano impostati su true.

**Viene visualizzato un testo di menu errato o il comando viene visualizzato nella posizione errata:**

- Assicurarsi che la combinazione di GUID e ID sia univoca per questo comando.

- Assicurarsi di aver disinstallato versioni precedenti del pacchetto.

## <a name="see-also"></a>Vedi anche

- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Procedura: Modificare un comando di menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Distribuzione di soluzioni per un linguaggio specifico di dominio](msi-and-vsix-deployment-of-a-dsl.md)
- [Codice di esempio: Diagrammi di circuito](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
