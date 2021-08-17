---
title: Associare un'area del modulo a una Outlook di messaggio
description: Informazioni su come specificare quali Microsoft Office Outlook visualizzare un'area del modulo associando l'area del modulo alla classe di messaggio di ogni elemento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f38640840b929b4044ca37d6571c82289f32b55f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038227"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associare un'area del modulo a una Outlook di messaggio
  È possibile specificare quali Microsoft Office Outlook visualizzare un'area del modulo associando l'area del modulo alla classe di messaggio di ogni elemento. Ad esempio, se si vuole aggiungere un'area del modulo alla fine di un elemento di posta, è possibile associare l'area del modulo alla `IPM.Note` classe di messaggio.

 Per associare un'area del modulo a una classe messaggio, specificare il nome della classe di messaggio **nella** procedura guidata Nuova area modulo Outlook o applicare un attributo alla classe factory dell'area del modulo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Informazioni Outlook classi di messaggio
 Una Outlook di messaggio identifica un tipo di Outlook elemento. Nella tabella seguente sono elencati questi otto tipi standard di elementi e i relativi nomi di classe di messaggio.

|Outlook Tipo di elemento|Nome classe messaggio|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` o `IPM.Post.RSS`|
| TaskItem|`IPM.Task`|

 È anche possibile specificare i nomi delle classi di messaggio personalizzate. Le classi di messaggio personalizzate identificano i moduli personalizzati definiti in Outlook.

> [!NOTE]
> Per le aree del modulo replacement e replace-all, è possibile specificare un nuovo nome di classe di messaggio personalizzato. Non è necessario usare il nome della classe messaggio di un modulo personalizzato esistente. Il nome della classe di messaggio personalizzata deve essere univoco. Un modo per assicurarsi che il nome sia univoco è usare una convenzione di denominazione simile alla seguente: \<*StandardMessageClassName*> \<*Company*> .\<*MessageClassName*> (ad esempio: `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associare un'area del modulo a una Outlook di messaggio
 Esistono due modi per associare un'area del modulo a una classe messaggio:

- Usare la **procedura guidata Nuova Outlook'area del modulo.**

- Applicare gli attributi della classe.

### <a name="use-the-new-outlook-form-region-wizard"></a>Usare la procedura guidata Nuova area Outlook modulo
 Nella pagina finale  della procedura guidata Nuova area del modulo Outlook è possibile selezionare classi di messaggi standard e digitare i nomi delle classi di messaggio personalizzate che si desidera associare all'area del modulo.

 Le classi di messaggio standard non sono disponibili se l'area del modulo è progettata per sostituire l'intero modulo o la pagina predefinita di un modulo. È possibile specificare nomi di classe di messaggio standard solo per i moduli che aggiungono una nuova pagina a un modulo o che vengono aggiunti alla fine di un modulo. Per altre informazioni, [vedere Procedura: Aggiungere un'area del modulo a](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)un progetto Outlook componente aggiuntivo .

 Per includere una o più classi messaggio personalizzate, digitarne i nomi nella casella Quali classi di messaggi personalizzate **verranno visualizzate nell'area del modulo?** .

 I nomi digitati devono essere conformi alle linee guida seguenti:

- Usare il nome completo della classe di messaggio( ad esempio: "IPM. Note.Contoso").

- Usare il punto e virgola per separare più nomi di classi di messaggio.

- Non includere classi di messaggio Outlook standard, ad esempio "IPM. Nota" o "IPM. Contatto". Includere solo classi di messaggio personalizzate, ad esempio "IPM. Note.Contoso".

- Non specificare la classe di messaggio di base da sola (ad esempio: "IPM").

- Non superare i 256 caratteri per ogni nome di classe di messaggio.

  La **procedura guidata Nuova Outlook'area del** modulo convalida il formato dell'input quando si fa clic su **Fine**.

> [!NOTE]
> La **procedura guidata Nuova Outlook'area del** modulo non verifica che i nomi delle classi di messaggio specificati siano corretti o validi.

 Al termine della procedura guidata, la procedura guidata Nuova area Outlook **modulo** applica gli attributi alla classe dell'area del modulo che contiene i nomi di classe di messaggio specificati. È anche possibile applicare questi attributi manualmente.

### <a name="apply-class-attributes"></a>Applicare attributi di classe
 È possibile associare un'area del modulo a una Outlook di messaggio dopo aver completato la procedura **guidata Nuova Outlook'area del modulo.** A tale scopo, applicare gli attributi alla classe factory dell'area del modulo.

 Nell'esempio seguente vengono illustrati due <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> attributi applicati a una classe factory dell'area del modulo denominata `myFormRegion` . Il primo attributo associa l'area del modulo a una classe di messaggio standard per un modulo di messaggio di posta elettronica. Il secondo attributo associa l'area del modulo a una classe di messaggio personalizzata denominata `IPM.Task.Contoso` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs" id="Snippet1":::

 Gli attributi devono essere conformi alle linee guida seguenti:

- Per le classi di messaggio personalizzate, usare il nome completo della classe di messaggio( ad esempio: "IPM. Note.Contoso").

- Non specificare la classe di messaggio di base da sola (ad esempio: "IPM").

- Non superare i 256 caratteri per ogni nome di classe di messaggio.

- Non includere i nomi delle classi di messaggio standard se l'area del modulo sostituisce l'intero modulo o la pagina predefinita di un modulo. È possibile specificare nomi di classe di messaggio standard solo per i moduli che aggiungono una nuova pagina a un modulo o che vengono aggiunti alla fine di un modulo. Per altre informazioni, [vedere Procedura: Aggiungere un'area del modulo a](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)un progetto Outlook componente aggiuntivo .

  Visual Studio convalida il formato dei nomi delle classi messaggio quando si compila il progetto.

> [!NOTE]
> Visual Studio verifica che i nomi delle classi messaggio specificati siano corretti o validi.

## <a name="see-also"></a>Vedi anche
- [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)
- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: Progettare un'area Outlook modulo](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Linee guida per creare aree Outlook modulo](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Panoramica del nome del modulo e della classe di messaggio](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Come Outlook moduli ed elementi](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
