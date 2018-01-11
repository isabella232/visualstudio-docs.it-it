---
title: Modificare lo stile degli oggetti in Blend | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0d01e7c8ef95270cde9c1054cc286b62bbe95c46
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="modify-the-style-of-objects-in-blend"></a>Modificare lo stile degli oggetti in Blend
Il modo più semplice per personalizzare un oggetto consiste nell'impostare le proprietà nel riquadro **Proprietà**.  
  
 Per riusare impostazioni o gruppi di impostazioni, creare una risorsa riutilizzabile, ovvero uno *stile*, un *modello* o qualcosa di semplice, come un colore personalizzato. È anche possibile impostare un controllo in modo che venga visualizzato in modo diverso a seconda dello stato, come ad esempio un pulsante che diventa verde quando viene selezionato dall'utente.  
  
 **Contenuto dell'argomento**:  
  
-   [Pennelli: modificare l'aspetto di un oggetto](#Brushes)  
  
-   [Stili e modelli: creare un aspetto coerente tra i vari controlli](#Styles)  
  
-   [Stati di visualizzazione: modificare l'aspetto di un controllo in base al relativo stato](#Visual)  
  
-   [Risorse: creare colori, stili e modelli e riutilizzarli in seguito](#Resources)  
  
##  <a name="Brushes"></a> Pennelli: modificare l'aspetto di un oggetto  
 Per modificare l'aspetto di un oggetto, è possibile applicarvi un pennello.  
  
 **Breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Editor di pennelli](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Disegnare un'immagine o un motivo ripetuto su un oggetto  
 Per disegnare un'immagine o un motivo ripetuto su un oggetto, è possibile usare un *pennello tessera*.  
  
 Per creare un pennello tessera, creare prima una risorsa *pennello immagine*, *pennello da disegno* o *pennello visivo*.  
  
 Per creare un pennello immagine, usare un'immagine. Le illustrazioni seguenti mostrano il pennello immagine, il pennello immagine affiancato e il pennello immagine capovolto.  
  
 ![](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31") ![](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2") ![](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png "38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")  
  
 Per creare un pennello da disegno, usare un disegno vettoriale, ad esempio un tracciato o una forma. Le illustrazioni seguenti mostrano il pennello da disegno, il pennello da disegno affiancato e il pennello da disegno capovolto.  
  
 ![](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5") ![](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc") ![](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png "15bf6021-620c-4490-9eae-086153d3f14f")  
  
 Per creare un pennello visivo, usare un controllo, ad esempio un pulsante. Le illustrazioni seguenti mostrano il pennello visivo e il pennello visivo affiancato.  
  
 ![](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227") ![](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")  
  
 **Breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Pennello tessera](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
##  <a name="Styles"></a> Stili e modelli: creare un aspetto coerente tra i vari controlli  
 È possibile progettare l'aspetto e il comportamento di un controllo una volta e applicarne le caratteristiche ad altri controlli in modo che non sia necessario gestirle singolarmente.  
  
 **Quando usare uno stile**: se si vogliono solo impostare le proprietà predefinite, come il colore di un pulsante, è preferibile usare uno *stile*. È possibile modificare un controllo anche dopo l'applicazione di uno stile.  
  
 **Quando usare un modello**: se si vuole modificare la struttura di un controllo, è preferibile usare un *modello*. Si supponga di voler convertire un elemento grafico o un logo in un pulsante. Non è possibile modificare un controllo dopo l'applicazione di un modello.  
  
### <a name="create-a-template-or-style"></a>Creare un modello o uno stile  
 È possibile creare un modello in due modi diversi. Si può convertire un oggetto qualsiasi presente nella tavola da disegno in un controllo oppure basare il modello su un controllo esistente.  
  
 Per convertire un oggetto qualsiasi in un modello di controllo, selezionare l'oggetto e quindi scegliere **Crea controllo** dal menu **Strumenti**.  
  
 Se si preferisce basare il modello su un controllo esistente, selezionare un oggetto nella tavola da disegno. Nella parte superiore della tavola da disegno fare clic sul pulsante di navigazione, scegliere **Modifica modello** e quindi **Modifica una copia** o **Crea vuoto**.  
  
 ![](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")  
  
 Per creare uno stile, selezionare l'oggetto, scegliere **Modifica stile** dal menu **Oggetto** e quindi **Modifica una copia** o **Crea vuoto**.  
  
-   Scegliere **Modifica una copia** per iniziare con lo stile o il modello predefinito del controllo.  
  
-   Scegliere **Crea vuoto** per partire da zero.  
  
 L'opzione **Modifica corrente** viene visualizzata solo se si modifica uno stile o un modello che è già stato creato. Non sarà invece visibile per un controllo che usa ancora un modello di sistema predefinito.  
  
 Nella finestra di dialogo **Create Style Resource** (Crea risorsa di stile) è possibile assegnare un nome allo stile o al modello per poterlo usare in seguito oppure applicare lo stile o il modello a tutti i controlli di tale tipo.  
  
 ![](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")  
  
> [!NOTE]
>  Non è possibile creare stili o modelli per ogni tipo di controllo. Se questi non sono supportati in un controllo, il pulsante di navigazione non verrà visualizzato sopra la tavola da disegno.  
>   
>  Per tornare all'ambito di modifica del documento principale, fare clic su **Reimposta l'ambito** ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4f20-aa66-a6f5b23eeb2b").  
>   
>  ![](../designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")  
  
 **Breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Creare uno stile](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95).  
  
 **Breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Creazione di un modello di controllo in Expression Blend](http://msdn.microsoft.com/expression/cc263912.aspx).  
  
### <a name="apply-a-style-or-template-to-a-control"></a>Applicare uno stile o un modello a un controllo  
 Fare clic con il pulsante destro del mouse su un oggetto nel pannello [Oggetti e sequenza temporale](http://msdn.microsoft.com/en-us/135a5a5e-ec6d-4f38-8827-60e284cd5f57), scegliere **Modifica modello** e quindi **Applica risorsa**.  
  
 ![](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")  
  
### <a name="restore-the-default-style-or-template-of-a-control"></a>Ripristinare lo stile o il modello predefinito di un controllo  
 Selezionare il controllo e nel pannello [Proprietà](http://msdn.microsoft.com/en-us/135a5a5e-ec6d-4f38-8827-60e284cd5f57) individuare la proprietà **Stile** o **Modello**. Fare clic su **Opzioni avanzate** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb") e quindi su **Reimposta** nel menu di scelta rapida.  
  
##  <a name="Visual"></a> Stati di visualizzazione: modificare l'aspetto di un controllo in base al relativo stato  
 L'aspetto visivo dei controlli può essere diverso in base alle interazioni dell'utente. Ad esempio, è possibile impostare un pulsante in modo che diventi verde quando un utente lo seleziona oppure fare in modo che venga eseguita un'animazione. Per abbreviare o prolungare l'intervallo tra gli stati visivi, si possono usare le transizioni.  
  
 ![](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")  
  
 **Breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Gestire lo stato dei controlli WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
##  <a name="Resources"></a> Risorse: creare colori, stili e modelli e riutilizzarli in seguito  
 È possibile convertire in una risorsa qualsiasi elemento del progetto. Una risorsa è in pratica un oggetto che è possibile riusare in parti diverse dell'applicazione. Ad esempio, è possibile creare un colore una volta, convertirlo in risorsa e quindi usarlo per più oggetti. Per modificare il colore di tutti gli oggetti, sarà quindi sufficiente modificare la risorsa colore.  
  
 ![](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-cf66-46e0-B153-52a23cd744f7") ![ ] (../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")  
  
 **Breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Introduzione alle risorse](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'interfaccia utente usando Blend per Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)