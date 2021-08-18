---
title: Aggiunta di icone ai comandi di menu | Microsoft Docs
description: Informazioni su come aggiungere icone ai comandi che possono essere visualizzati sia nei menu che nelle barre degli strumenti nell'ambiente Visual Studio di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c6ffca49ee3b3c89293be9d9bbc18ebf3f1bb0fe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035306"
---
# <a name="add-icons-to-menu-commands"></a>Aggiungere icone ai comandi di menu
I comandi possono essere visualizzati sia nei menu che nelle barre degli strumenti. Nelle barre degli strumenti è comune che un comando venga visualizzato con solo un'icona (per risparmiare spazio) mentre nei menu viene in genere visualizzato un comando con un'icona e un testo.

 Le icone hanno una larghezza di 16 pixel per 16 pixel di altezza e possono essere a 8 bit (256 colori) o a 32 bit (colore vero). Sono preferibili le icone a colori a 32 bit. Le icone vengono in genere disposte in una singola riga orizzontale in una singola bitmap, anche se sono consentite più bitmap. Questa bitmap viene dichiarata nel file *con estensione vsct* insieme alle singole icone disponibili nella bitmap. Per altri dettagli, vedere le informazioni di riferimento per l'elemento [Bitmaps.](../extensibility/bitmaps-element.md)

## <a name="add-an-icon-to-a-command"></a>Aggiungere un'icona a un comando
 La procedura seguente presuppone che si abbia un progetto VSPackage esistente con un comando di menu. Per informazioni su come eseguire questa operazione, vedere [Creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Creare una bitmap con una profondità di colore di 32 bit. Un'icona è sempre 16 x 16, quindi questa bitmap deve avere un'altezza di 16 pixel e un multiplo di 16 pixel di larghezza.

     Ogni icona viene posizionata sulla bitmap una accanto all'altra in una singola riga. Usare il canale alfa per indicare le posizioni di trasparenza in ogni icona.

     Se si usa una profondità di colore a 8 bit, usare magenta, `RGB(255,0,255)` , come trasparenza. Tuttavia, sono preferibili le icone a colori a 32 bit.

2. Copiare il file dell'icona nella directory *Resources* nel progetto VSPackage. Nel **Esplora soluzioni** aggiungere l'icona al progetto. Selezionare Risorse **e** scegliere Aggiungi dal menu di scelta **rapida,** quindi **Elemento esistente** e selezionare il file dell'icona.

3. Aprire il file *vsct* nell'editor.

4. Aggiungere un `GuidSymbol` elemento con il nome **testIcon**. Creare un GUID (**Strumenti** Crea GUID , quindi selezionare Formato registro e fare clic su  >   **Copia**) e incollarlo  `value` nell'attributo. Il risultato dovrebbe essere simile al seguente:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Aggiungere un `<IDSymbol>` oggetto per l'icona. `name`L'attributo è l'ID dell'icona e indica la posizione sulla `value` striscia, se presente. Se è presente una sola icona, aggiungere 1. Il risultato dovrebbe essere simile al seguente:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Creare un `<Bitmap>` oggetto nella sezione del file con estensione `<Bitmaps>` *vsct* per rappresentare la bitmap contenente le icone.

    - Impostare il `guid` valore sul nome `<GuidSymbol>` dell'elemento creato nel passaggio precedente.

    - Impostare il `href` valore sul percorso relativo del file bitmap (in questo caso Risorse<nome file **\\ dell'icona \>**.

    - Impostare il `usedList` valore su IDSymbol creato in precedenza. Questo attributo specifica un elenco delimitato da virgole delle icone da usare nel pacchetto VSPackage. Le icone non presenti nell'elenco vengono escluse dalla compilazione del modulo.

         Il blocco Bitmap dovrebbe essere simile al seguente:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Nell'elemento `<Button>` esistente impostare `Icon` l'elemento ai valori GUIDSymbol e IDSymbol creati in precedenza. Ecco un esempio di elemento Button con questi valori:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Testare l'icona. Compilare il progetto e avviare il debug. Nell'istanza sperimentale trovare il comando . Dovrebbe essere visualizzata l'icona aggiunta.

## <a name="see-also"></a>Vedi anche
- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Informazioni di riferimento sullo schema XML VSCT](../extensibility/vsct-xml-schema-reference.md)
