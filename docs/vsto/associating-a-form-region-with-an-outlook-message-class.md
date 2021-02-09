---
title: Associare un'area del modulo a una classe messaggio di Outlook
description: Informazioni su come specificare quali Microsoft Office elementi di Outlook visualizzano un'area del modulo associando l'area del modulo alla classe Message di ogni elemento.
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
ms.openlocfilehash: 0bbbd381ff84714b780bbb817ccfea64ac05e949
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882544"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associare un'area del modulo a una classe messaggio di Outlook
  È possibile specificare quali Microsoft Office elementi di Outlook visualizzano un'area del modulo associando l'area del modulo alla classe Message di ogni elemento. Se ad esempio si desidera aggiungere un'area del modulo alla parte inferiore di un elemento di posta elettronica, è possibile associare l'area del modulo alla `IPM.Note` classe Message.

 Per associare un'area del modulo a una classe Message, specificare il nome della classe messaggio nella procedura guidata **nuova area del modulo di Outlook** o applicare un attributo alla classe factory dell'area del modulo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Informazioni sulle classi di messaggi di Outlook
 Una classe messaggio di Outlook identifica un tipo di elemento di Outlook. Nella tabella seguente sono elencati questi otto tipi standard di elementi e i relativi nomi di classe messaggio.

|Tipo di elemento di Outlook|Nome della classe messaggio|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` o `IPM.Post.RSS`|
| TaskItem|`IPM.Task`|

 È inoltre possibile specificare i nomi delle classi di messaggi personalizzate. Le classi di messaggi personalizzate identificano i moduli personalizzati definiti in Outlook.

> [!NOTE]
> Per le aree del modulo di sostituzione e di sostituzione di tutti, è possibile specificare un nuovo nome di classe messaggio personalizzato. Non è necessario usare il nome della classe messaggio di un modulo personalizzato esistente. Il nome della classe messaggio personalizzata deve essere univoco. Un modo per assicurarsi che il nome sia univoco consiste nell'usare una convenzione di denominazione simile alla seguente: \<*StandardMessageClassName*> . \<*Company*> .\<*MessageClassName*> (ad esempio: `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associare un'area del modulo a una classe messaggio di Outlook
 Esistono due modi per associare un'area del modulo a una classe Message:

- Utilizzare la procedura guidata **nuova area del modulo di Outlook** .

- Applicare gli attributi della classe.

### <a name="use-the-new-outlook-form-region-wizard"></a>Usare la procedura guidata nuova area del modulo di Outlook
 Nella pagina finale della procedura guidata **nuova area del modulo di Outlook** è possibile selezionare classi messaggio standard e digitare i nomi delle classi di messaggi personalizzate che si desidera associare all'area del modulo.

 Le classi di messaggio standard non sono disponibili se l'area del modulo è progettata per sostituire l'intero form o la pagina predefinita di un modulo. È possibile specificare nomi di classi di messaggio standard solo per i moduli che aggiungono una nuova pagina a un form o che vengono aggiunti alla fine di un form. Per altre informazioni, vedere [procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Per includere una o più classi di messaggi personalizzate, digitare i nomi nella casella in **cui le classi di messaggi personalizzate visualizzeranno questa area del modulo?** .

 I nomi digitati devono essere conformi alle linee guida seguenti:

- Utilizzare il nome completo della classe messaggio (ad esempio: "IPM. Nota. contoso ").

- Usare i punti e virgola per separare più nomi di classi di messaggio.

- Non includere classi di messaggi di Outlook standard, ad esempio "IPM. Nota "o" IPM. Contattare ". Includere solo classi di messaggi personalizzate, ad esempio "IPM". Nota. contoso ".

- Non specificare la classe del messaggio di base in modo autonomo (ad esempio: "IPM").

- Non superare i 256 caratteri per ogni nome di classe messaggio.

  La procedura guidata **nuova area del modulo di Outlook** consente di convalidare il formato dell'input quando si fa clic su **fine**.

> [!NOTE]
> La procedura guidata **nuova area del modulo di Outlook** non verifica che i nomi delle classi di messaggi forniti siano corretti o validi.

 Al termine della procedura guidata, la procedura guidata **nuova area del modulo di Outlook** applica gli attributi alla classe dell'area del modulo che contiene i nomi delle classi di messaggi specificati. È anche possibile applicare questi attributi manualmente.

### <a name="apply-class-attributes"></a>Applicare gli attributi della classe
 È possibile associare un'area del modulo a una classe messaggio di Outlook dopo aver completato la procedura guidata **nuova area del modulo di Outlook** . A tale scopo, applicare gli attributi alla classe factory dell'area del modulo.

 Nell'esempio seguente vengono illustrati due <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> attributi che sono stati applicati a una classe factory dell'area del modulo denominata `myFormRegion` . Il primo attributo associa l'area del modulo a una classe di messaggio standard per un modulo di messaggio di posta elettronica. Il secondo attributo associa l'area del modulo a una classe di messaggio personalizzata denominata `IPM.Task.Contoso` .

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 Gli attributi devono essere conformi alle linee guida seguenti:

- Per le classi di messaggi personalizzate, usare il nome completo della classe messaggio (ad esempio: "IPM. Nota. contoso ").

- Non specificare la classe del messaggio di base in modo autonomo (ad esempio: "IPM").

- Non superare i 256 caratteri per ogni nome di classe messaggio.

- Non includere i nomi delle classi di messaggio standard se l'area del modulo sostituisce l'intero form o la pagina predefinita di un form. È possibile specificare nomi di classi di messaggio standard solo per i moduli che aggiungono una nuova pagina a un form o che vengono aggiunti alla fine di un form. Per altre informazioni, vedere [procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

  Visual Studio convalida il formato dei nomi di classe messaggio quando si compila il progetto.

> [!NOTE]
> Visual Studio non verifica che i nomi delle classi di messaggi forniti siano corretti o validi.

## <a name="see-also"></a>Vedi anche
- [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)
- [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Linee guida per la creazione di aree del modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Cenni preliminari su nome modulo e classe messaggio](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Interazione tra gli elementi e i form di Outlook](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
