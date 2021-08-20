---
title: Linee guida per la creazione di aree Outlook modulo
description: Informazioni sulle linee guida per la creazione di aree Outlook modulo che consentono di ottimizzare le aree del modulo ed evitare potenziali problemi.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e357126554169c54faa53fdd8810cf040851fc2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130481"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Linee guida per creare aree Outlook modulo
  Le informazioni seguenti consentono di ottimizzare le aree del modulo ed evitare potenziali problemi:

- [Usare i nomi delle aree del modulo](#UsingFormRegions).

- [Disabilitare l'ereditarietà dell'area del modulo.](#DisablingInheritance)

- [Informazioni su tipi e nomi di classi di messaggio](#ClassNames).

- [Progettare aree del modulo adiacenti per il riquadro di lettura.](#ReadingPane)

- [Usare le dimensioni ottimali delle icone](#UsingOptimal).

  Per altre informazioni sulle aree del modulo, vedere [Creare Outlook modulo](../vsto/creating-outlook-form-regions.md).

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="use-form-region-names"></a><a name="UsingFormRegions"></a> Usare i nomi delle aree del modulo
 Per descrivere l'area del modulo possono essere usati diversi nomi. È importante comprendere la differenza tra questi nomi e gli effetti che hanno sull'area del modulo. La tabella seguente descrive i singoli nomi.

|Nome dell'area del modulo|Descrizione|
|----------------------|-----------------|
|Nome dell'elemento dell'area del modulo|Il nome specificato per l'elemento **Area del modulo di Outlook** nella finestra di dialogo **Aggiungi nuovo elemento** . È il nome del file di codice dell'area del modulo visualizzato in **Esplora soluzioni**.|
|Proprietà<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>|Questo nome viene specificato nella pagina **Fornire un testo descrittivo e selezionare le preferenze di visualizzazione** della procedura guidata **Nuova area del modulo di Outlook** . Questo nome viene visualizzato come proprietà **FormRegionName** nella finestra **Proprietà** .<br /><br /> Usare la proprietà <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> per specificare l'etichetta che identifica l'area del modulo nell'interfaccia utente di Outlook. Per le aree del modulo separate, questo nome viene visualizzato come pulsante nella barra multifunzione dell'elemento di Outlook.<br /><br /> Per le aree del modulo adiacenti, questo nome viene visualizzato come testo di intestazione sopra l'area del modulo.|
|Attributo `Microsoft.Office.Tools.Outlook.FormRegionName`|Quando si aggiunge un elemento **Area del modulo di Outlook** al progetto, Visual Studio imposta questa proprietà sul nome completo dell'area del modulo. Il nome completo predefinito è il nome del componente aggiuntivo VSTO connesso al nome dell'area del modulo con un punto, ad esempio `OutlookAddIn1.FormRegion1`.<br /><br /> Questo nome completo viene visualizzato anche come attributo nella parte superiore della classe factory dell'area del modulo.<br /><br /> Usare `Microsoft.Office.Tools.Outlook.FormRegionName` l'attributo per identificare in modo univoco l'area del modulo in Outlook VSTO componenti aggiuntivi. Non è possibile modificare il valore `Microsoft.Office.Tools.Outlook.FormRegionName` dell'attributo rinominando l'elemento dell'area del modulo o modificando la <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> proprietà . Per cambiare questo nome, è necessario modificare l'attributo `Microsoft.Office.Tools.Outlook.FormRegionName` nel file di codice dell'area del modulo.|

## <a name="disable-form-region-inheritance"></a><a name="DisablingInheritance"></a> Disabilitare l'ereditarietà dell'area del modulo
 Per impostazione predefinita, una classe messaggio personalizzata eredita tutte le associazioni dell'area del modulo per la classe messaggio di base. Ad esempio, una classe messaggio denominata `IPM.Task.Contoso` deriva da `IPM.Task`. Quindi, `IPM.Task.Contoso` eredita le associazioni dell'area del modulo di `IPM.Task`.

 Per non associare l'area del modulo con classi messaggio derivate, impostare la proprietà <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> dell'area del modulo su **true**. Ad esempio, se si associa un'area del modulo adiacente a e si imposta la proprietà su true , l'area del modulo verrà aggiunta solo alla fine di un `IPM.Task` <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> modulo attività standard.  L'area del modulo non verrà aggiunta alla fine di versioni personalizzate di un modulo di attività standard.

## <a name="understand-types-and-message-class-names"></a><a name="ClassNames"></a> Informazioni su tipi e nomi di classi messaggio
 Il nome del tipo di un elemento di Outlook è diverso dal nome della classe messaggio di un elemento di Outlook. Ad esempio, il nome del tipo di un elemento RSS è `Microsoft.Office.Interop.Outlook.PostItem`. Il nome della classe messaggio di un elemento RSS è `IPM.Post.RSS`.

 Usare il nome del tipo per fare riferimento a un elemento di Outlook nel codice. Per un elenco di nomi di tipo, vedere [Associare un'area del modulo a una Outlook message class](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

 Usare il nome della classe messaggio degli elementi di Outlook nella procedura guidata **Nuova area del modulo di Outlook** per associare l'elemento all'area del modulo. Per un elenco di nomi di classi di messaggio validi, vedere [Associare un'area](../vsto/associating-a-form-region-with-an-outlook-message-class.md)del modulo a una Outlook message class .

## <a name="design-adjoining-form-regions-for-the-reading-pane"></a><a name="ReadingPane"></a> Progettare aree del modulo adiacenti per il riquadro di lettura
 È possibile usare il riquadro di lettura di Outlook per visualizzare l'anteprima di un elemento di Outlook senza aprirlo. Il riquadro di lettura è progettato solo per l'accesso in lettura. Quindi, i controlli di input aggiunti a un'area del modulo adiacente, ad esempio una casella di testo, potrebbero non funzionare come previsto quando l'elemento e l'area del modulo sono aperti nel riquadro di lettura.

 Ad esempio, se un elemento con un'area del modulo adiacente è aperto nel riquadro di lettura, è possibile che si verifichi la situazione seguente:

1. Selezionare il testo in una casella di testo nell'area del modulo.

2. Premere **CANC.**

3. Non viene eliminato il testo nella casella di testo, ma l'intero elemento di posta elettronica.

   Se si sta progettando un'area del modulo adiacente che contiene controlli di input, testare i controlli nel riquadro di lettura per verificarne il corretto funzionamento. Valutare l'aggiunta di codice personalizzato per disabilitare i controlli che non funzionano come previsto.

   In alternativa, è possibile impostare la proprietà <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> dell'area del modulo su **False**. In questo modo, l'area del modulo non può essere usata nel riquadro di lettura.

## <a name="use-optimal-icon-sizes"></a><a name="UsingOptimal"></a> Usare dimensioni ottimali delle icone
 Per specificare quali icone visualizzare nell'area del modulo, impostare le proprietà dell'icona nel gruppo di proprietà **Icone** della finestra **Proprietà** . Usare le linee guida seguenti per ottenere la migliore qualità grafica possibile:

- Per l'icona **Pagina** , usare un file PNG (Portable Network Graphics).

- Per l'icona **Finestra** si consiglia una dimensione di 32 pixel per 32 pixel.

- Per tutte le altre icone, le dimensioni consigliate sono 16 pixel per 16 pixel.

  L'icona **Pagina** viene visualizzata nella barra multifunzione di un controllo per gli elementi con aree del modulo separate, di sostituzione o di sostituzione completa.

  **L'icona** Finestra viene visualizzata nell'area di notifica e nella finestra **di** dialogo ALT TAB per gli elementi aperti che visualizzano aree del modulo di sostituzione o +  sostituzione di tutte.

## <a name="see-also"></a>Vedi anche
- [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)
- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: Progettare un'area Outlook modulo](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procedura: Aggiungere un'area del modulo a un progetto Outlook componente aggiuntivo](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Associare un'area del modulo a una Outlook di messaggio](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
