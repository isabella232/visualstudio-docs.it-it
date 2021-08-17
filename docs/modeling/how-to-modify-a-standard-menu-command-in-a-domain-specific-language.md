---
title: Modificare il comando di menu standard in DSL
description: Informazioni su come modificare il comportamento di alcuni dei comandi standard definiti automaticamente nel DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 744c52dc23a7f144a42c371abc7faab520c58226f488a04540bd590c8965c2d2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428952"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Procedura: modificare un comando di menu standard in un linguaggio specifico di dominio

È possibile modificare il comportamento di alcuni comandi standard definiti automaticamente nel linguaggio DSL. Ad esempio, è possibile modificare **Taglia** in modo che escludi le informazioni riservate. Per modificare i comandi, si esegue l'override dei metodi in una classe di set di comandi. Queste classi sono definite nel file CommandSet.cs, nel progetto DslPackage, e derivano da <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

> [!NOTE]
> Per creare comandi di menu personalizzati, vedere [Procedura: Aggiungere un comando al menu di scelta rapida.](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)

## <a name="what-commands-can-you-modify"></a>Comandi modificabili

### <a name="to-discover-what-commands-you-can-modify"></a>Per trovare i comandi modificabili

1. Nel progetto `DslPackage` aprire `GeneratedCode\CommandSet.cs`. Questo file C# è disponibile in Esplora soluzioni come sussidiaria di `CommandSet.tt` .

2. Trovare le classi in questo file i cui nomi terminano con " `CommandSet` ", ad esempio `Language1CommandSet` e `Language1ClipboardCommandSet` .

3. In ogni classe di set di comandi digitare "`override`" seguito da uno spazio. IntelliSense mostrerà un elenco dei metodi di cui è possibile eseguire l'override. Ogni comando ha una coppia di metodi i cui nomi iniziano con "`ProcessOnStatus`" e "`ProcessOnMenu`".

4. Prendere nota delle classi di set di comandi contenenti il comando che si vuole modificare.

5. Chiudere il file senza salvare le modifiche.

    > [!NOTE]
    > In genere, è opportuno non modificare i file che sono stati generati. Eventuali modifiche andranno perse la volta successiva che i file verranno generati.

## <a name="extend-the-appropriate-command-set-class"></a>Estendere la classe di set di comandi appropriata

Creare un nuovo file contenente una dichiarazione parziale della classe di set di comandi.

### <a name="to-extend-the-command-set-class"></a>Per estendere la classe di set di comandi

1. In Esplora soluzioni, nel progetto DslPackage aprire la cartella GeneratedCode, cercare in CommandSet.tt e aprire il file CommandSet.cs generato. Prendere nota dello spazio dei nomi e del nome della prima classe definita qui. Può, ad esempio, essere visualizzato:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. In **DslPackage** creare una cartella denominata **Codice personalizzato**. In questa cartella creare un nuovo file di classe denominato `CommandSet.cs` .

3. Nel nuovo file scrivere una dichiarazione parziale con lo stesso spazio dei nomi e lo stesso nome della classe parziale generata. Esempio:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

    > [!NOTE]
    > Se è stato usato il modello di file di classe per creare il nuovo file, è necessario correggere sia lo spazio dei nomi che il nome della classe.

## <a name="override-the-command-methods"></a>Eseguire l'override dei metodi dei comandi

La maggior parte dei comandi ha due metodi associati: il metodo con un nome come `ProcessOnStatus` ... determina se il comando deve essere visibile e abilitato. Viene chiamato quando l'utente fa clic con il pulsante destro del mouse sul diagramma e deve essere eseguito rapidamente e senza apportare modifiche. `ProcessOnMenu`... viene chiamato quando l'utente fa clic sul comando e deve eseguire la funzione del comando. Potrebbe essere necessario eseguire l'override di uno o entrambi i metodi.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Per cambiare la situazione in cui il comando viene visualizzato in un menu

Eseguire l'override di ProcessOnStatus... Metodo. Questo metodo deve impostare le proprietà Visible ed Enabled del parametro MenuCommand. In genere il comando esamina this.CurrentSelection per determinare se il comando si applica agli elementi selezionati, di cui può anche esaminare le proprietà per determinare se può essere applicato con il loro stato corrente.

In generale, la proprietà Visible deve essere determinata dagli elementi selezionati. La proprietà Enabled, che determina se il comando viene visualizzato in nero o in grigio nel menu, deve dipendere dallo stato corrente della selezione.

L'esempio seguente disabilita la voce di menu Delete quando l'utente seleziona più di una forma.

> [!NOTE]
> Se il comando è disponibile con una pressione di tasto, questo metodo non impedisce di usarlo. Ad esempio, anche se si disabilita la voce di menu Delete, il comando può ugualmente essere richiamato con CANC.

```csharp
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

Eseguire l'override di ProcessOnMenu... Metodo. L'esempio seguente impedisce all'utente di eliminare più di un elemento per volta, anche usando CANC.

```csharp
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

Se il codice apporta modifiche all'archivio, ad esempio creando, eliminando o aggiornando elementi o collegamenti, è necessario farlo in una transazione. Per altre informazioni, vedere [Come creare e aggiornare gli elementi del modello.](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

### <a name="write-the-code-of-the-methods"></a>Scrivere il codice dei metodi

I frammenti seguenti sono spesso utili in questi metodi:

- `this.CurrentSelection`. La forma su cui l'utente ha fatto clic con il pulsante destro del mouse viene sempre inclusa nell'elenco di forme e connettori. Se l'utente fa clic su una parte vuota del diagramma, il diagramma è l'unico membro dell'elenco.

- `this.IsDiagramSelected()` - `true` se l'utente ha fatto clic su una parte vuota del diagramma.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` - L'utente non ha selezionato più forme

- `this.SingleSelection` : forma o diagramma su cui l'utente ha fatto clic con il pulsante destro del mouse

- `shape.ModelElement as MyLanguageElement` : elemento del modello rappresentato da una forma.

Per altre informazioni su come spostarsi da un elemento all'altro e su come creare oggetti e collegamenti, vedere Esplorazione e aggiornamento di un modello [nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Vedi anche

- <xref:System.ComponentModel.Design.MenuCommand>
- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Procedura: aggiungere un comando al menu di scelta rapida](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimenti sullo schema XML VSCT](../extensibility/vsct-xml-schema-reference.md)
- [Esempio di VMSDK - Circuit Diagrams. Personalizzazione DSL completa](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
