---
title: Aggiunta di icone ai comandi di menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9f038dc43c1705a7cef47eb09a17607c535e307
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903433"
---
# <a name="add-icons-to-menu-commands"></a>Aggiungere icone ai comandi di menu
I comandi possono essere visualizzati sia nei menu che nelle barre degli strumenti. Sulle barre degli strumenti è normale che un comando venga visualizzato solo con un'icona (per risparmiare spazio) mentre nei menu un comando viene in genere visualizzato con un'icona e un testo.

 Le icone sono di 16 pixel di larghezza per 16 pixel di altezza e possono avere una profondità di colore a 8 bit (colori 256) o una profondità di colore a 32 bit (true color). sono preferite le icone a colori a 32 bit. Le icone vengono in genere disposte in una singola riga orizzontale in un'unica bitmap, sebbene siano consentite più bitmap. Questa bitmap viene dichiarata nel file con *estensione vsct* insieme alle singole icone disponibili nella bitmap. Per ulteriori informazioni, vedere il riferimento per l' [elemento bitmap](../extensibility/bitmaps-element.md) .

## <a name="add-an-icon-to-a-command"></a>Aggiungere un'icona a un comando
 Nella procedura seguente si presuppone che sia presente un progetto VSPackage esistente con un comando di menu. Per informazioni su come eseguire questa operazione, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Creare una bitmap con una profondità di colore di 32 bit. Un'icona è sempre 16 x 16, quindi questa bitmap deve avere una larghezza massima di 16 pixel e un multiplo di 16 pixel di larghezza.

     Ogni icona viene posizionata nella bitmap accanto l'una all'altra in un'unica riga. Usare il canale alfa per indicare le posizioni di trasparenza in ogni icona.

     Se si utilizza una profondità di colore a 8 bit, utilizzare magenta `RGB(255,0,255)` come trasparenza. Tuttavia, le icone a colori a 32 bit sono preferite.

2. Copiare il file icona nella directory *Resources* nel progetto VSPackage. Nella **Esplora soluzioni**aggiungere l'icona al progetto. (Selezionare **risorse**, quindi nel menu di scelta rapida fare clic su **Aggiungi**, quindi su **elemento esistente**e selezionare il file dell'icona).

3. Aprire il file con *estensione vsct* nell'editor.

4. Aggiungere un `GuidSymbol` elemento con il nome **testIcon**. Creare un GUID (**strumenti**  >  **Crea GUID**, quindi selezionare il **formato del registro di sistema** e fare clic su **copia**) e incollarlo nell' `value` attributo. Il risultato dovrebbe essere simile al seguente:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Aggiungere un oggetto `<IDSymbol>` per l'icona. L' `name` attributo è l'ID dell'icona e indica la `value` relativa posizione nell'eventuale striscia. Se è presente solo un'icona, aggiungere 1. Il risultato dovrebbe essere simile al seguente:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Creare un oggetto `<Bitmap>` nella `<Bitmaps>` sezione del file con *estensione vsct* per rappresentare la bitmap contenente le icone.

    - Impostare il `guid` valore sul nome dell' `<GuidSymbol>` elemento creato nel passaggio precedente.

    - Impostare il `href` valore sul percorso relativo del file bitmap (in questo caso **risorse \\<\> nome file icona**.

    - Impostare il `usedList` valore su IDSymbol creato in precedenza. Questo attributo specifica un elenco delimitato da virgole delle icone da usare nel pacchetto VSPackage. Le icone non presenti nell'elenco sono escluse dalla compilazione del modulo.

         Il blocco bitmap dovrebbe essere simile al seguente:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Nell'elemento esistente `<Button>` impostare l'elemento sui `Icon` valori GUIDSymbol e IDSymbol creati in precedenza. Di seguito è riportato un esempio di un elemento Button con i valori seguenti:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Testare l'icona. Compilare il progetto e avviare il debug. Nell'istanza sperimentale, trovare il comando. Dovrebbe essere visualizzata l'icona aggiunta.

## <a name="see-also"></a>Vedere anche
- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Riferimento XML Schema VSCT](../extensibility/vsct-xml-schema-reference.md)
