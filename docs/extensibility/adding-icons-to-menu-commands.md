---
title: Aggiunta di icone ai comandi di Menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c54ee6b448e5830b478f10029a0d2d958e7699
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352368"
---
# <a name="add-icons-to-menu-commands"></a>Aggiungere le icone ai comandi di menu
I comandi possono apparire su entrambi i menu e barre degli strumenti. Nelle barre degli strumenti, è comune per un comando da visualizzare solo un'icona (per risparmiare spazio) mentre nei menu che con un'icona e il testo visualizzato in genere un comando.

 Le icone sono 16 pixel di larghezza per 16 pixel di altezza e possono essere intensità di colore 8 bit (256 colori) o la profondità di colore di 32 bit (colore true). le icone di colori a 32 bit sono preferite. Le icone vengono disposte in genere in una singola riga orizzontale in una singola bitmap, anche se sono consentite più immagini bitmap. Questa bitmap viene dichiarata nel *vsct* file insieme le singole icone disponibili nella bitmap. Vedere le informazioni di riferimento per la [elemento Bitmaps](../extensibility/bitmaps-element.md) per altri dettagli.

## <a name="add-an-icon-to-a-command"></a>Aggiungere un'icona per un comando
 La procedura seguente si presuppone di avere un progetto VSPackage esistente con un comando di menu. Per scoprire come eseguire questa operazione, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Creare una bitmap con intensità di colore di 32 bit. Un'icona è sempre pari a 16x16, pertanto questa bitmap deve essere 16 pixel di altezza e multipli di 16 pixel di larghezza.

     Ogni icona viene posizionato sulla bitmap uno accanto a altro in una singola riga. Usare il canale alfa per indicare posizioni di trasparenza in ogni icona.

     Se si usa una profondità di colore a 8 bit, usare magenta, `RGB(255,0,255)`, come la trasparenza. Tuttavia, le icone di colori a 32 bit sono preferite.

2. Copiare il file dell'icona per il *risorse* directory del progetto di VSPackage. Nel **Esplora soluzioni**, aggiungere l'icona per il progetto. (Selezionare **le risorse**e menu di scelta rapida fare clic su **Add**, quindi **elemento esistente**e selezionare il file icona.)

3. Aprire il *vsct* file nell'editor.

4. Aggiungere un `GuidSymbol` elemento con il nome **testIcon**. Creare un GUID (**degli strumenti** > **Crea GUID**, quindi selezionare **formato del Registro di sistema** e fare clic su **copia**) e incollarlo nel `value` attributo. Il risultato dovrebbe essere simile al seguente:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Aggiungere un `<IDSymbol>` dell'icona. Il `name` attributo è l'ID dell'icona e il `value` indica la posizione nella striscia di, se presente. Se è presente una sola icona, aggiungere 1. Il risultato dovrebbe essere simile al seguente:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Creare un `<Bitmap>` nel `<Bitmaps>` sezione il *con estensione vsct* file per rappresentare la mappa di bit contenente le icone.

    - Impostare il `guid` valore per il nome del `<GuidSymbol>` elemento è stato creato nel passaggio precedente.

    - Impostare il `href` valore per il percorso relativo del file bitmap (in questo caso **risorse\\< nome file dell'icona\>** .

    - Impostare il `usedList` valore per il IDSymbol creato in precedenza. Questo attributo specifica un elenco delimitato da virgole delle icone da utilizzare nel pacchetto VSPackage. Le icone non inclusi nell'elenco sono esclusi form compilazione.

         Il blocco di Bitmap dovrebbe essere simile al seguente:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Esistente `<Button>` elemento, impostare il `Icon` elemento ai valori GUIDSymbol e IDSymbol creato in precedenza. Di seguito è riportato un esempio di un elemento Button con tali valori:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Verificare l'icona. Compilare il progetto e avviare il debug. Nell'istanza sperimentale, trovare il comando. Viene visualizzata l'icona che è stato aggiunto.

## <a name="see-also"></a>Vedere anche
- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Riferimento allo schema XML VSCT](../extensibility/vsct-xml-schema-reference.md)