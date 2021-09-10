---
title: EditorConfig
description: Uso di un file editorconfig per consentire stili di scrittura codice del progetto coerenti in Visual Studio per Mac.
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.topic: how-to
ms.openlocfilehash: c7269b4272fb8ed2c73dbe9f57e94da071dc623e
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964432"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Creazione e modifica di un file EditorConfig personalizzato

In Visual Studio per Mac è possibile aggiungere un file [EditorConfig](https://editorconfig.org/) al progetto o alla soluzione per imporre stili di codifica coerenti per tutti gli utenti che usano la codebase. Le impostazioni dichiarate nel file EditorConfig hanno la precedenza sulle impostazioni dell'editor di testo di Visual Studio per Mac globali. L'uso di un file EditorConfig all'interno del progetto o della codebase consente di impostare lo stile di scrittura del codice, le preferenze e gli avvisi per il progetto. Poiché il file fa parte della codebase, rende più semplice per tutti gli utenti rispettare le procedure di scrittura del codice per un progetto, indipendentemente dall'IDE o dall'editor di codice usato.

I file [EditorConfig](https://editorconfig.org/) sono supportati in molti IDE e editor di codice, compreso Visual Studio.

## <a name="supported-settings"></a>Impostazioni supportate

L'editor in Visual Studio per Mac supporta il set di base delle [proprietà di EditorConfig](https://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig supporta anche [convenzioni per la scrittura di codice](/visualstudio/ide/editorconfig-code-style-settings-reference) in C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Aggiungere un file EditorConfig a un progetto

### <a name="adding-a-new-editorconfig-file"></a>Aggiunta di un nuovo file EditorConfig

1. Aprire il progetto in Visual Studio per Mac. Selezionare il nodo della soluzione o del progetto a cui si desidera aggiungere il file EditorConfig. L'aggiunta del file alla directory della soluzione consente di applicare le impostazioni di editorconfig a tutti i progetti nella soluzione.

2. Fare clic con il pulsante destro del mouse sul nodo e scegliere **Aggiungi > Nuovo file** per aprire la finestra di dialogo **Nuovo file**:

    ![Voci di menu del contenuto](media/editorconfig-image0.png)

3. Scegliere **> file di testo vuoto** e assegnargli il **nome** `.editorconfig` . Premere **Nuovo** per creare il file e aprirlo nell'editor:

    ![Finestra di dialogo Nuovo file](media/editorconfig-image1.png)

    Aggiungere automaticamente l'elemento a livello di soluzione consente di crearlo e annidarlo in una cartella **Elementi di soluzione**:

    ![Elemento della soluzione visualizzato nella finestra della soluzione](media/editorconfig-image1a.png)

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

4. Le impostazioni dal file `.editorconfig` verranno applicate a qualsiasi nuovo codice scritto, ma il codice esistente potrebbe dover essere riformattato per renderlo coerente con le nuove impostazioni. Per applicare le impostazioni dal file `.editorconfig` a un file di origine esistente, aprire il file e scegliere **Modifica > Formato > Formatta documento** dalla barra dei menu:

    ![Voce di menu Formatta documento](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Aggiunta di un file EditorConfig esistente

Se si sta lavorando a un progetto o a una soluzione contenente già un file `.editorconfig`, per applicare le impostazioni non è necessaria alcuna operazione. Tutte le nuove righe di codice vengono formattate in base alle impostazioni del file EditorConfig.

Nel progetto è consigliabile riusare un file `.editorconfig` esistente. Per aggiungere un file esistente, eseguire le operazioni seguenti:

1. Fare clic con il pulsante destro del mouse sulla cartella a cui si vuole aggiungerla e **> Aggiungi file**.

2. Passare alla directory del file richiesto.

3. I file che iniziano con `.` (ad esempio `.editorconfig`) sono file nascosti in macOS, quindi premere **Comando + Maiuscole +.** per rendere il file `.editorconfig` visibile.

4. Selezionare il `.editorconfig` file e fare clic su **Apri:**

    ![Finestra per l'aggiunta di un nuovo file](media/editorconfig-image3b.png)

5. Quando viene visualizzata la finestra di dialogo seguente, selezionare l'opzione **Copia file nella directory** e selezionare **OK**:

    ![Opzioni della finestra di dialogo per aggiungere un file a una cartella](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Aggiornare le impostazioni dal file EditorConfig

Dopo aver aggiunto un file EditorConfig alla codebase, qualsiasi nuovo codice aggiunto viene formattato automaticamente in base alle impostazioni specificate. Il codice esistente non rispecchia automaticamente le impostazioni a meno che non si formatti la codebase.

Per aggiornare le impostazioni con quelle del file `.editorconfig`, selezionare il nodo della soluzione e scegliere **Modifica > Formato > Formatta documento** dalla barra dei menu:

![Formatta documento dalla barra dei menu](media/editorconfig-image3a.png)

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

Se si imposta `root` su `true`, il file viene contrassegnato come file di livello più alto della codebase e qualsiasi altro file `.editorconfig` di livello superiore nel progetto viene ignorato, come spiegato nella sezione [Eseguire l'override delle impostazioni di EditorConfig](#override-editorconfig-settings).

Ogni sezione, identificata da parentesi quadre (**[ ]**), specifica le informazioni sui tipi di file interessati dalle proprietà che seguono.

Nell'esempio precedente, alcune impostazioni vengono applicate a tutti i file del progetto e altre vengono aggiunte solo ai file C#. Gli screenshot riportati di seguito illustrano la situazione prima e dopo l'applicazione delle impostazioni di `.editorconfig`:

**Prima di**:

![Prima dell'applicazione delle impostazioni del file editorconfig](media/editorconfig-image4.png)

**Dopo**:

![Dopo l'applicazione delle impostazioni del file editorconfig](media/editorconfig-image5.png)

Per altre informazioni sulle impostazioni di EditorConfig disponibili, vedere l'articolo [Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig](/visualstudio/ide/editorconfig-code-style-settings-reference) e la sezione [Supported Properties](https://editorconfig.org/#supported-properties) (Proprietà supportate) nella documentazione ufficiale.

## <a name="override-editorconfig-settings"></a>Eseguire l'override delle impostazioni di EditorConfig

Per ogni soluzione è possibile avere più file `.editorconfig`. Visual Studio per Mac legge i file `.editorconfig` dall'alto verso il basso nella soluzione, aggiungendo ed eseguendo l'override delle impostazioni man mano. Questo significa che le impostazioni nel file `.editorconfig` _più vicine_ al file in corso di modifica avranno la precedenza. Le impostazioni vengono recuperate dal file `.editorconfig` nella stessa cartella (se presente), poi dal file `.editorconfig` nella cartella padre (se presente) e così via finché non si raggiunge `root=true`.

Per assicurarsi che _nessuna_ impostazione di alcun file `.editorconfig` di livello superiore sia applicata a questa parte della codebase, aggiungere la proprietà `root=true` all'inizio del file `.editorconfig` di livello inferiore:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Vedi anche

- [Creare impostazioni personalizzate per l'editor con EditorConfig (Visual Studio in Windows)](/visualstudio/ide/create-portable-custom-editor-options)