---
title: EditorConfig
description: Uso di un file editorconfig per consentire stili di scrittura codice del progetto coerenti in Visual Studio per Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 336ec5ef0779bcd67302bea7b51851dced531a7d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Creazione e modifica di un file EditorConfig personalizzato

In Visual Studio per Mac è possibile aggiungere un file [EditorConfig](http://editorconfig.org/) al progetto o alla codebase per imporre stili di codifica coerenti per tutti gli utenti che usano la codebase. Le impostazioni dichiarate nel file EditorConfig hanno la precedenza sulle impostazioni dell'editor di testo di Visual Studio globali. L'uso di EditorConfig all'interno del progetto o della codebase consente di impostare lo stile di scrittura codice, le preferenze e gli avvisi per il progetto. In questo modo per tutti gli utenti di Visual Studio per Mac è più semplice rispettare le procedure di scrittura codice del progetto.

I file [EditorConfig](http://editorconfig.org/) sono supportati in molti IDE ed editor di codice, compreso Visual Studio 2017. 

## <a name="supported-settings"></a>Impostazioni supportate

L'editor in Visual Studio supporta il set di base delle [proprietà di EditorConfig](http://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig supporta anche la [formattazione dello stile del codice](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) in C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Aggiungere un file EditorConfig a un progetto

### <a name="adding-a-new-editorconfig-file"></a>Aggiunta di un nuovo file EditorConfig

1. Aprire il progetto in Visual Studio per Mac. Selezionare il nodo del progetto a cui si vogliono aggiungere file.

2. Con il nodo selezionato, passare a **File > Nuovo file...** nella barra dei menu per aprire la finestra di dialogo **Nuovo file**.

3. Scegliere **Varie > File di testo vuoto** e assegnare a questo il **nome** `.editorconfig`. Premere **Nuovo** per creare il file e aprirlo nell'editor:

    ![Finestra di dialogo Nuovo file](media/editorconfig-image1.png)

4. Modificare il file. Ad esempio:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. L'aggiunta del file non implica l'aggiornamento automatico delle impostazioni. Per aggiornare le impostazioni con quelle del file `.editorconfig`, selezionare il nodo del progetto e scegliere **Modifica > Formato > Formatta documento** dalla barra dei menu:

    ![Voce di menu Formatta documento](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Aggiunta di un file EditorConfig esistente

Se si sta lavorando a un progetto o a una soluzione contenente già un file `.editorconfig`, per applicare le impostazioni non è necessaria alcuna operazione. Tutte le nuove righe di codice vengono formattate in base alle impostazioni del file EditorConfig. Si noti che, nonostante Visual Studio per Mac rispetti i file `.editorconfig` a livello di soluzione, i file possono non essere visualizzati nel riquadro della soluzione, perché in macOS i file che iniziano con `.` sono nascosti.

Nel progetto è consigliabile riusare un file `.editorconfig` esistente. Per aggiungere un file esistente, è prima necessario visualizzare i file nascosti in Finder immettendo il comando seguente nel **terminale**:

```bash
$ defaults write com.apple.Finder AppleShowAllFiles true
$ killall Finder
```

Quando il file `.editorconfig` è visibile, trascinarlo sul nodo del progetto. Quando viene visualizzata la finestra di dialogo seguente, selezionare l'opzione **Copia file nella directory** e selezionare **OK**:

![Voce di menu Formatta documento](media/editorconfig-image3.png)

Per riflettere le impostazioni del file `.editorconfig`, selezionare il nodo del progetto e scegliere **Modifica > Formato > Formatta documento** dalla barra dei menu.

## <a name="editing-an-editorconfig-file"></a>Modifica di un file EditorConfig

Per specificare le impostazioni, i file EditorConfig usano un layout di file semplice, descritto di seguito tramite un esempio precedente:


```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Se si imposta `root` su `true`, il file viene contrassegnato come file di livello più alto della codebase e qualsiasi altro file `.editorconfig` di livello superiore nel progetto verrà ignorato, come spiegato nella sezione [Eseguire l'override delle impostazioni di EditorConfig](#override-editorconfig-settings).

Ogni sezione, identificata da parentesi quadre (**[ ]**), specifica le informazioni sui tipi di file interessati dalle proprietà che seguono.

Nell'esempio precedente, alcune impostazioni vengono applicate a tutti i file del progetto e altre vengono aggiunte solo ai file C#. Gli screenshot riportati di seguito illustrano la situazione prima e dopo l'applicazione delle impostazioni di `.editorconfig`:

**Prima**:

![Prima dell'applicazione delle impostazioni del file editorconfig](media/editorconfig-image4.png)

**Dopo**:

![Dopo l'applicazione delle impostazioni del file editorconfig](media/editorconfig-image5.png)

Per altre informazioni sulle impostazioni di EditorConfig disponibili, vedere l'articolo [Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) e la sezione [Supported Properties](http://editorconfig.org/#supported-properties) (Proprietà supportate) nella documentazione ufficiale.

## <a name="override-editorconfig-settings"></a>Eseguire l'override delle impostazioni di EditorConfig

Per ogni soluzione è possibile avere più file `.editorconfig`. Visual Studio for Mac legge i file `.editorconfig` dall'alto verso il basso nella soluzione, aggiungendo ed eseguendo l'override delle impostazioni man mano. Ciò significa che le impostazioni nel file `.editorconfig` _più vicino_ al file che si sta modificando hanno la precedenza. 

Per assicurarsi che _nessuna_ impostazione di alcun file `.editorconfig` di livello superiore sia applicata a questa parte della codebase, aggiungere la proprietà `root=true` all'inizio del file `.editorconfig` di livello inferiore:

```EditorConfig
# top-most EditorConfig file
root = true
```