---
title: 'Procedura: modificare un comando di menu standard in una Domain-Specific Language | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 989367d395abb56e4f57c4aa2694b5f4ef17fb6e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300871"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Procedura: modificare un comando di menu standard in un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare il comportamento di alcuni comandi standard definiti automaticamente nel linguaggio DSL. Ad esempio, è possibile modificare il **taglio** in modo che escluda le informazioni riservate. Per modificare i comandi, si esegue l'override dei metodi in una classe di set di comandi. Queste classi sono definite nel file CommandSet.cs, nel progetto DslPackage, e derivano da <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

 In sintesi, per modificare un comando:

1. [Individuare i comandi che è possibile modificare](#what).

2. [Creare una dichiarazione parziale della classe del set di comandi appropriata](#extend).

3. [Eseguire l'override dei metodi ProcessOnStatus e metodo](#override) per il comando.

   In questo argomento viene illustrata la procedura.

> [!NOTE]
> Se si desidera creare comandi di menu personalizzati, vedere [procedura: aggiungere un comando al menu di scelta rapida](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what"></a>Quali comandi è possibile modificare?

#### <a name="to-discover-what-commands-you-can-modify"></a>Per trovare i comandi modificabili

1. Nel progetto `DslPackage` aprire `GeneratedCode\CommandSet.cs`. È C# possibile trovare questo file in Esplora soluzioni come filiale di `CommandSet.tt`.

2. Trovare le classi in questo file i cui nomi terminano con "`CommandSet`", ad esempio `Language1CommandSet` e `Language1ClipboardCommandSet`.

3. In ogni classe di set di comandi digitare "`override`" seguito da uno spazio. IntelliSense mostrerà un elenco dei metodi di cui è possibile eseguire l'override. Ogni comando ha una coppia di metodi i cui nomi iniziano con "`ProcessOnStatus`" e "`ProcessOnMenu`".

4. Prendere nota delle classi di set di comandi contenenti il comando che si vuole modificare.

5. Chiudere il file senza salvare le modifiche.

    > [!NOTE]
    > In genere, è opportuno non modificare i file che sono stati generati. Eventuali modifiche andranno perse la volta successiva che i file verranno generati.

## <a name="extend"></a>Estendere la classe del set di comandi appropriata
 Creare un nuovo file contenente una dichiarazione parziale della classe di set di comandi.

#### <a name="to-extend-the-command-set-class"></a>Per estendere la classe di set di comandi

1. In Esplora soluzioni, nel progetto DslPackage aprire la cartella GeneratedCode, cercare in CommandSet.tt e aprire il file CommandSet.cs generato. Prendere nota dello spazio dei nomi e del nome della prima classe definita qui. Può, ad esempio, essere visualizzato:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. In **DslPackage**creare una cartella denominata **codice personalizzato**. In questa cartella creare un nuovo file di classe denominato `CommandSet.cs`.

3. Nel nuovo file scrivere una dichiarazione parziale con lo stesso spazio dei nomi e lo stesso nome della classe parziale generata. Ad esempio:

    ```
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

     **Nota** Se è stato usato il modello di file di classe per creare il nuovo file, è necessario correggere sia lo spazio dei nomi sia il nome della classe.

## <a name="override"></a>Eseguire l'override dei metodi di comando
 Alla maggior parte dei comandi sono associati due metodi: il metodo con un nome come `ProcessOnStatus`... determina se il comando deve essere visibile e abilitato. Viene chiamato quando l'utente fa clic con il pulsante destro del mouse sul diagramma e deve essere eseguito rapidamente e senza apportare modifiche. `ProcessOnMenu`... viene chiamato quando l'utente fa clic sul comando e deve eseguire la funzione del comando. Potrebbe essere necessario eseguire l'override di uno o entrambi i metodi.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Per cambiare la situazione in cui il comando viene visualizzato in un menu
 Eseguire l'override di ProcessOnStatus... Metodo. Questo metodo deve impostare le proprietà Visible ed Enabled del parametro MenuCommand. In genere il comando esamina this.CurrentSelection per determinare se il comando si applica agli elementi selezionati, di cui può anche esaminare le proprietà per determinare se può essere applicato con il loro stato corrente.

 In generale, la proprietà Visible deve essere determinata dagli elementi selezionati. La proprietà Enabled, che determina se il comando viene visualizzato in nero o in grigio nel menu, deve dipendere dallo stato corrente della selezione.

 L'esempio seguente disabilita la voce di menu Delete quando l'utente seleziona più di una forma.

> [!NOTE]
> Se il comando è disponibile con una pressione di tasto, questo metodo non impedisce di usarlo. Ad esempio, anche se si disabilita la voce di menu Delete, il comando può ugualmente essere richiamato con CANC.

```
/// <summary>
/// Called when user right-clicks on the diagram or clicks the Edit menu.
/// </summary>
/// <param name="command">Set Visible and Enabled properties.</param>
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)
{
  // Default settings from the base method.
  base.ProcessOnStatusDeleteCommand(command);
  if (this.CurrentSelection.Count > 1)
  {
    // If user has selected more than one item, Delete is greyed out.
    command.Enabled = false;
  }
}
```

 È consigliabile chiamare prima il metodo di base, per gestire tutti i casi e le impostazioni che non costituiscono un problema.

 Il metodo ProcessOnStatus non deve creare, eliminare o aggiornare elementi nell'archivio.

### <a name="to-change-the-behavior-of-the-command"></a>Per cambiare il comportamento del comando
 Eseguire l'override di metodo... Metodo. L'esempio seguente impedisce all'utente di eliminare più di un elemento per volta, anche usando CANC.

```
/// <summary>
/// Called when user presses Delete key
/// or clicks the Delete command on a menu.
/// </summary>
protected override void ProcessOnMenuDeleteCommand()
{
  // Allow users to delete only one thing at a time.
  if (this.CurrentSelection.Count <= 1)
  {
    base.ProcessOnMenuDeleteCommand();
  }
}
```

 Se il codice apporta modifiche all'archivio, ad esempio creando, eliminando o aggiornando elementi o collegamenti, è necessario farlo in una transazione. Per ulteriori informazioni, vedere [come creare e aggiornare elementi del modello](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="writing-the-code-of-the-methods"></a>Scrittura del codice dei metodi
 I frammenti seguenti sono spesso utili in questi metodi:

- `this.CurrentSelection` La forma su cui l'utente ha fatto clic con il pulsante destro del mouse viene sempre inclusa nell'elenco di forme e connettori. Se l'utente fa clic su una parte vuota del diagramma, il diagramma è l'unico membro dell'elenco.

- `this.IsDiagramSelected()` - `true` se l'utente ha fatto clic su una parte vuota del diagramma.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()`-l'utente non ha selezionato più forme

- `this.SingleSelection`: la forma o il diagramma su cui l'utente ha fatto clic con il pulsante destro del mouse

- `shape.ModelElement as MyLanguageElement`: elemento del modello rappresentato da una forma.

  Per ulteriori informazioni su come passare da un elemento all'altro e su come creare oggetti e collegamenti, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Vedere anche
 <xref:System.ComponentModel.Design.MenuCommand> [scrivere codice per personalizzare una Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md) [procedura: aggiungere un comando al menu di scelta rapida](../modeling/how-to-add-a-command-to-the-shortcut-menu.md) [procedura dettagliata: recupero di informazioni da un collegamento selezionato](../misc/walkthrough-getting-information-from-a-selected-link.md) [come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md) [Visual Studio tabella dei comandi (. File vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [vsct XML Schema Reference](../extensibility/vsct-xml-schema-reference.md)
