---
title: Aggiunta di icone ai comandi di Menu | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 051fc6b33a04870f0d21e14ecbe0adc8fcd525be
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526839"
---
# <a name="adding-icons-to-menu-commands"></a>Aggiunta di icone ai comandi di menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [aggiunta di icone ai comandi di Menu](https://docs.microsoft.com/visualstudio/extensibility/adding-icons-to-menu-commands).  
  
I comandi possono apparire su entrambi i menu e barre degli strumenti. Nelle barre degli strumenti, è comune per un comando da visualizzare solo un'icona (per risparmiare spazio) mentre nei menu che con un'icona e il testo visualizzato in genere un comando.  
  
 Le icone sono 16 pixel di larghezza per 16 pixel di altezza e possono essere intensità di colore 8 bit (256 colori) o la profondità di colore di 32 bit (colore true). le icone di colori a 32 bit sono preferite. Le icone vengono disposte in genere in una singola riga orizzontale in una singola bitmap, anche se sono consentite più immagini bitmap. Questa bitmap viene dichiarata nel file con estensione vsct insieme le singole icone disponibili nella bitmap. Vedere le informazioni di riferimento per la [elemento Bitmaps](../extensibility/bitmaps-element.md) per altri dettagli.  
  
## <a name="adding-an-icon-to-a-command"></a>Aggiunta di un'icona per un comando  
 La procedura seguente si presuppone di avere un progetto VSPackage esistente con un comando di menu. Per scoprire come eseguire questa operazione, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Creare una bitmap con intensità di colore di 32 bit. Un'icona è sempre pari a 16x16, pertanto questa bitmap deve essere 16 pixel di altezza e multipli di 16 pixel di larghezza.  
  
     Ogni icona viene posizionato sulla bitmap uno accanto a altro in una singola riga. Usare il canale alfa per indicare posizioni di trasparenza in ogni icona.  
  
     Se si usa una profondità di colore a 8 bit, usare magenta, `RGB(255,0,255)`, come la trasparenza. Tuttavia, le icone di colori a 32 bit sono preferite.  
  
2.  Copiare il file dell'icona per la directory delle risorse nel progetto VSPackage. In Esplora soluzioni, l'icona Aggiungi al progetto. (Selezionare le risorse e nel menu di scelta rapida fare clic su Aggiungi, quindi l'elemento esistente e selezionare il file icona.)  
  
3.  Aprire il file con estensione vsct nell'editor.  
  
4.  Aggiungere un `GuidSymbol` elemento con il nome **testIcon**. Creare un GUID (**strumenti / creare GUID**, quindi selezionare **formato del Registro di sistema** e scegliere Copia) e incollarlo nella `value` attributo. Il risultato dovrebbe essere simile al seguente:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Aggiungere un `<IDSymbol>` dell'icona. Il `name` attributo è l'ID dell'icona e il `value` indica la posizione nella striscia di, se presente. Se è presente una sola icona, aggiungere 1. Il risultato dovrebbe essere simile al seguente:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Creare un `<Bitmap>` nella `<Bitmaps>` sezione del file con estensione vsct per rappresentare la mappa di bit contenente le icone.  
  
    -   Impostare il `guid` valore per il nome del `<GuidSymbol>` elemento è stato creato nel passaggio precedente.  
  
    -   Impostare il `href` valore per il percorso relativo del file bitmap (in questo caso **risorse\\< nome file dell'icona\>**.  
  
    -   Impostare il `usedList` valore per il IDSymbol creato in precedenza. Questo attributo specifica un elenco delimitato da virgole delle icone da utilizzare nel pacchetto VSPackage. Le icone non inclusi nell'elenco sono esclusi form compilazione.  
  
         Il blocco di Bitmap dovrebbe essere simile al seguente:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Esistente `<Button>` elemento, impostare il `Icon` elemento ai valori GUIDSymbol e IDSymbol creato in precedenza. Di seguito è riportato un esempio di un elemento Button con tali valori:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Verificare l'icona. Compilare il progetto e avviare il debug. Nell'istanza sperimentale, trovare il comando. Viene visualizzata l'icona che è stato aggiunto.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Riferimenti sullo schema XML VSCT](../extensibility/vsct-xml-schema-reference.md)

