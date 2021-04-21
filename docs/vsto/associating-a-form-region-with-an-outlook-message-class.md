---
title: Associare un'area del modulo a una classe di messaggio di Outlook
description: Informazioni su come specificare quali elementi Microsoft Office Outlook visualizzano un'area del modulo associando l'area del modulo alla classe di messaggio di ogni elemento.
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
ms.workload:
- office
ms.openlocfilehash: be3b789fabf00d853d447cb3489ef07a5b494fcd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826993"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associare un'area del modulo a una classe di messaggio di Outlook
  È possibile specificare Microsoft Office elementi di Outlook che visualizzano un'area del modulo associando l'area del modulo alla classe di messaggio di ogni elemento. Ad esempio, se si vuole aggiungere un'area del modulo alla fine di un elemento di posta elettronica, è possibile associare l'area del modulo alla `IPM.Note` classe di messaggio.

 Per associare un'area del modulo a una classe messaggio, specificare il nome della classe di messaggio nella procedura guidata Nuova area del modulo di **Outlook** o applicare un attributo alla classe factory dell'area del modulo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Informazioni su classi di messaggi di Outlook
 Una classe di messaggio di Outlook identifica un tipo di elemento di Outlook. Nella tabella seguente sono elencati questi otto tipi standard di elementi e i relativi nomi di classe di messaggio.

|Tipo di elemento di Outlook|Nome classe messaggio|
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

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associare un'area del modulo a una classe messaggio di Outlook
 Esistono due modi per associare un'area del modulo a una classe messaggio:

- Usare la **procedura guidata Nuova area del modulo di Outlook.**

- Applicare gli attributi della classe.

### <a name="use-the-new-outlook-form-region-wizard"></a>Usare la procedura guidata Nuova area del modulo di Outlook
 Nella pagina finale della procedura guidata Nuova area del modulo di **Outlook** è possibile selezionare classi di messaggi standard e digitare i nomi delle classi messaggio personalizzate da associare all'area del modulo.

 Le classi di messaggio standard non sono disponibili se l'area del modulo è progettata per sostituire l'intero modulo o la pagina predefinita di un modulo. È possibile specificare nomi di classe messaggio standard solo per i moduli che aggiungono una nuova pagina a un modulo o che vengono aggiunti alla fine di un modulo. Per altre informazioni, vedere [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook.](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

 Per includere una o più classi di messaggio personalizzate, digitarne i nomi nella casella Quali classi di messaggi personalizzate **visualizzano l'area del modulo?** .

 I nomi digitati devono essere conformi alle linee guida seguenti:

- Usare il nome completo della classe messaggio(ad esempio: "IPM. Note.Contoso").

- Usare il punto e virgola per separare più nomi di classi di messaggio.

- Non includere classi di messaggi standard di Outlook, ad esempio "IPM. Nota" o "IPM. Contact". Includere solo classi di messaggi personalizzate, ad esempio "IPM. Note.Contoso".

- Non specificare la classe messaggio di base da sola (ad esempio: "IPM").

- Non superare i 256 caratteri per ogni nome di classe di messaggio.

  La **procedura guidata Nuova area del modulo** di Outlook convalida il formato dell'input quando si fa clic su **Fine.**

> [!NOTE]
> La **procedura guidata Nuova area del modulo di Outlook** non verifica che i nomi delle classi di messaggio specificati siano corretti o validi.

 Al termine della procedura guidata, la procedura guidata **Nuova area del** modulo di Outlook applica gli attributi alla classe dell'area del modulo che contiene i nomi delle classi di messaggio specificati. È anche possibile applicare questi attributi manualmente.

### <a name="apply-class-attributes"></a>Applicare attributi di classe
 È possibile associare un'area del modulo a una classe messaggio di Outlook dopo aver completato la **procedura guidata Nuova area del modulo di Outlook.** A tale scopo, applicare gli attributi alla classe factory dell'area del modulo.

 Nell'esempio seguente vengono illustrati due <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> attributi applicati a una classe factory dell'area del modulo denominata `myFormRegion` . Il primo attributo associa l'area del modulo a una classe di messaggio standard per un modulo di messaggio di posta elettronica. Il secondo attributo associa l'area del modulo a una classe di messaggio personalizzata denominata `IPM.Task.Contoso` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs" id="Snippet1":::

 Gli attributi devono essere conformi alle linee guida seguenti:

- Per le classi di messaggio personalizzate, usare il nome completo della classe di messaggio( ad esempio: "IPM. Note.Contoso").

- Non specificare la classe di messaggio di base da sola (ad esempio: "IPM").

- Non superare i 256 caratteri per ogni nome di classe di messaggio.

- Non includere i nomi delle classi di messaggio standard se l'area del modulo sostituisce l'intero modulo o la pagina predefinita di un modulo. È possibile specificare nomi di classe di messaggio standard solo per i moduli che aggiungono una nuova pagina a un modulo o che vengono aggiunti alla fine di un modulo. Per altre informazioni, [vedere Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook.](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

  Visual Studio convalida il formato dei nomi delle classi messaggio quando si compila il progetto.

> [!NOTE]
> Visual Studio verifica che i nomi delle classi messaggio specificati siano corretti o validi.

## <a name="see-also"></a>Vedi anche
- [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)
- [Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: Progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Linee guida per la creazione di aree del modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Panoramica del nome del modulo e della classe messaggio](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Modalità di utilizzo di moduli ed elementi di Outlook](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
