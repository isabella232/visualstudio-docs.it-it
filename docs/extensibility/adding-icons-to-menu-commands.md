---
title: Aggiunta di icone ai comandi di menu Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f4b71f981472451766f526cf62e975e571cf46da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740160"
---
# <a name="add-icons-to-menu-commands"></a>Aggiungere icone ai comandi di menu
I comandi possono essere visualizzati sia nei menu che nelle barre degli strumenti. Sulle barre degli strumenti, è comune che un comando venga visualizzato con solo un'icona (per risparmiare spazio) mentre nei menu viene in genere visualizzato un comando sia con un'icona che con il testo.

 Le icone hanno una larghezza di 16 pixel per un'altezza di 16 pixel e possono avere una profondità di colore a 8 bit (256 colori) o una profondità di colore a 32 bit (colore reale). Le icone a colori a 32 bit sono preferite. Le icone sono in genere disposte in una singola riga orizzontale in una singola bitmap, anche se sono consentite più bitmap. Questa bitmap viene dichiarata nel file *vsct* insieme alle singole icone disponibili nella bitmap. Vedere il riferimento per il [Bitmaps elemento](../extensibility/bitmaps-element.md) per ulteriori dettagli.

## <a name="add-an-icon-to-a-command"></a>Aggiungere un'icona a un comando
 La procedura seguente presuppone che si dispone di un progetto VSPackage esistente con un comando di menu. Per informazioni su come eseguire questa operazione, vedere [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu .

1. Creare una bitmap con una profondità di colore di 32 bit. Un'icona è sempre 16 x 16, quindi questa bitmap deve avere un'altezza di 16 pixel e un multiplo di 16 pixel di larghezza.

     Ogni icona viene posizionata sulla bitmap una accanto all'altra in un'unica riga. Utilizzare il canale alfa per indicare i punti di trasparenza in ogni icona.

     Se si utilizza una profondità di colore `RGB(255,0,255)`a 8 bit, utilizzare magenta, , come trasparenza. Tuttavia, le icone a colori a 32 bit sono preferite.

2. Copiare il file di icona nella directory *Resources* nel progetto VSPackage. In **Esplora soluzioni**aggiungere l'icona al progetto. Selezionare **Risorse**e nel menu di scelta rapida fare clic su **Aggiungi**, quindi **Elemento esistente**e selezionare il file di icona.

3. Aprire il file *vsct* nell'editor.

4. Aggiungere `GuidSymbol` un elemento con il nome **testIcon**. Creare un GUID (**Strumenti** > **Per creare GUID),** selezionare Formato `value` **Registro** di sistema e fare clic su **Copia**e incollarlo nell'attributo. Il risultato dovrebbe essere simile al seguente:The result should look like this:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Aggiungere `<IDSymbol>` un per l'icona. L'attributo `name` è l'ID dell'icona e indica `value` la sua posizione sulla striscia, se presente. Se è presente una sola icona, aggiungere 1. Il risultato dovrebbe essere simile al seguente:The result should look like this:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Creare `<Bitmap>` un `<Bitmaps>` nella sezione del file *vsct* per rappresentare la bitmap contenente le icone.

    - Impostare `guid` il valore sul `<GuidSymbol>` nome dell'elemento creato nel passaggio precedente.

    - Impostare `href` il valore sul percorso relativo del file bitmap (in questo caso **Resources\\<nome\>** del file icona .

    - Impostare `usedList` il valore per il IDSymbol creato in precedenza. Questo attributo specifica un elenco delimitato da virgole delle icone da utilizzare nel pacchetto VSPackage. Le icone non presenti nell'elenco sono escluse per la compilazione del modulo.

         Il blocco Bitmap dovrebbe essere simile al seguente:The Bitmap block should look like this:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Nell'elemento `<Button>` esistente impostare l'elemento `Icon` sui valori GUIDSymbol e IDSymbol creati in precedenza. Ecco un esempio di un Button elemento con tali valori:Here's an example of a Button element with those values:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Testare l'icona. Compilare il progetto e avviare il debug. Nell'istanza sperimentale, individuare il comando. Dovrebbe mostrare l'icona che hai aggiunto.

## <a name="see-also"></a>Vedere anche
- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Riferimento allo schema XML VSCT](../extensibility/vsct-xml-schema-reference.md)
