---
title: Linee guida per la creazione di aree del modulo di Outlook
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d48a3ad24d094d0ebc822b572f2521eaefae5356
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039922"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Linee guida per creare aree del modulo di Outlook
  Le informazioni seguenti consentono di ottimizzare le aree del modulo ed evitare potenziali problemi:

- [Usare nomi di aree modulo](#UsingFormRegions).

- [Disabilita ereditarietà dell'area del modulo](#DisablingInheritance).

- [Informazioni sui tipi e i nomi delle classi di messaggi](#ClassNames).

- [Progettazione aree del modulo per il riquadro di lettura adiacenti](#ReadingPane).

- [Usare dimensioni dell'icona ottimali](#UsingOptimal).

  Per altre informazioni sulle aree del modulo, vedere [aree del modulo Outlook creare](../vsto/creating-outlook-form-regions.md).

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="UsingFormRegions"></a> Usare i nomi delle aree di form
 Per descrivere l'area del modulo possono essere usati diversi nomi. È importante comprendere la differenza tra questi nomi e gli effetti che hanno sull'area del modulo. La tabella seguente descrive i singoli nomi.

|Nome dell'area del modulo|Descrizione|
|----------------------|-----------------|
|Nome dell'elemento dell'area del modulo|Il nome specificato per l'elemento **Area del modulo di Outlook** nella finestra di dialogo **Aggiungi nuovo elemento** . È il nome del file di codice dell'area del modulo visualizzato in **Esplora soluzioni**.|
|Proprietà<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> |Questo nome viene specificato nella pagina **Fornire un testo descrittivo e selezionare le preferenze di visualizzazione** della procedura guidata **Nuova area del modulo di Outlook** . Questo nome viene visualizzato come proprietà **FormRegionName** nella finestra **Proprietà** .<br /><br /> Usare la proprietà <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> per specificare l'etichetta che identifica l'area del modulo nell'interfaccia utente di Outlook. Per le aree del modulo separate, questo nome viene visualizzato come pulsante nella barra multifunzione dell'elemento di Outlook.<br /><br /> Per le aree del modulo adiacenti, questo nome viene visualizzato come testo di intestazione sopra l'area del modulo.|
|`Microsoft.Office.Tools.Outlook.FormRegionName` Attributo|Quando si aggiunge un elemento **Area del modulo di Outlook** al progetto, Visual Studio imposta questa proprietà sul nome completo dell'area del modulo. Il nome completo predefinito è il nome del componente aggiuntivo VSTO connesso al nome dell'area del modulo con un punto, ad esempio `OutlookAddIn1.FormRegion1`.<br /><br /> Questo nome completo viene visualizzato anche come attributo nella parte superiore della classe factory dell'area del modulo.<br /><br /> Usare l'attributo `Microsoft.Office.Tools.Outlook.FormRegionName` per identificare in modo univoco l'area del modulo tra tutti i componenti aggiuntivi VSTO di Outlook. Non è possibile modificare il valore dell'attributo `Microsoft.Office.Tools.Outlook.FormRegionName` rinominando l'elemento dell'area del modulo o modificando la proprietà <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>. Per cambiare questo nome, è necessario modificare l'attributo `Microsoft.Office.Tools.Outlook.FormRegionName` nel file di codice dell'area del modulo.|

## <a name="DisablingInheritance"></a> Disabilita ereditarietà dell'area del modulo
 Per impostazione predefinita, una classe messaggio personalizzata eredita tutte le associazioni dell'area del modulo per la classe messaggio di base. Ad esempio, una classe messaggio denominata `IPM.Task.Contoso` deriva da `IPM.Task`. Quindi, `IPM.Task.Contoso` eredita le associazioni dell'area del modulo di `IPM.Task`.

 Per non associare l'area del modulo con classi messaggio derivate, impostare la proprietà <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> dell'area del modulo su **true**. Ad esempio, se si associa un'area del modulo adiacente con `IPM.Task` e impostare il <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> proprietà **true**, solo l'area del modulo verrà aggiunto alla fine di un modulo di attività standard. L'area del modulo non verrà aggiunta alla fine di versioni personalizzate di un modulo di attività standard.

## <a name="ClassNames"></a> Comprendere i tipi e i nomi delle classi messaggio
 Il nome del tipo di un elemento di Outlook è diverso dal nome della classe messaggio di un elemento di Outlook. Ad esempio, il nome del tipo di un elemento RSS è `Microsoft.Office.Interop.Outlook.PostItem`. Il nome della classe messaggio di un elemento RSS è `IPM.Post.RSS`.

 Usare il nome del tipo per fare riferimento a un elemento di Outlook nel codice. Per un elenco di nomi di tipo, vedere [associare un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

 Usare il nome della classe messaggio degli elementi di Outlook nella procedura guidata **Nuova area del modulo di Outlook** per associare l'elemento all'area del modulo. Per un elenco di nomi delle classi messaggio validi, vedere [associare un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="ReadingPane"></a> Progettazione aree del modulo adiacenti per il riquadro di lettura
 È possibile usare il riquadro di lettura di Outlook per visualizzare l'anteprima di un elemento di Outlook senza aprirlo. Il riquadro di lettura è progettato solo per l'accesso in lettura. Quindi, i controlli di input aggiunti a un'area del modulo adiacente, ad esempio una casella di testo, potrebbero non funzionare come previsto quando l'elemento e l'area del modulo sono aperti nel riquadro di lettura.

 Ad esempio, se un elemento con un'area del modulo adiacente è aperto nel riquadro di lettura, è possibile che si verifichi la situazione seguente:

1. Selezionare il testo in una casella di testo nell'area del modulo.

2. Premere **Elimina**.

3. Non viene eliminato il testo nella casella di testo, ma l'intero elemento di posta elettronica.

   Se si sta progettando un'area del modulo adiacente che contiene controlli di input, testare i controlli nel riquadro di lettura per verificarne il corretto funzionamento. Valutare l'aggiunta di codice personalizzato per disabilitare i controlli che non funzionano come previsto.

   In alternativa, è possibile impostare la proprietà <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> dell'area del modulo su **False**. In questo modo, l'area del modulo non può essere usata nel riquadro di lettura.

## <a name="UsingOptimal"></a> Usare dimensioni dell'icona ottimali
 Per specificare quali icone visualizzare nell'area del modulo, impostare le proprietà dell'icona nel gruppo di proprietà **Icone** della finestra **Proprietà** . Usare le linee guida seguenti per ottenere la migliore qualità grafica possibile:

- Per l'icona **Pagina** , usare un file PNG (Portable Network Graphics).

- Per l'icona**Finestra** si consiglia una dimensione di 32 pixel per 32 pixel.

- Per tutte le altre icone, le dimensioni consigliate sono 16 pixel per 16 pixel.

  L'icona **Pagina** viene visualizzata nella barra multifunzione di un controllo per gli elementi con aree del modulo separate, di sostituzione o di sostituzione completa.

  Il **finestra** icona viene visualizzata nell'area di notifica e nella **Alt**+**scheda** finestra di dialogo per aprire gli elementi di tale visualizzazione sostituzione o di modulo di sostituzione aree.

## <a name="see-also"></a>Vedere anche
- [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)
- [Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: Progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Associare un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
