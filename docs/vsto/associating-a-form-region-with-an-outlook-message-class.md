---
title: Associare un'area del modulo a una classe messaggio di Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: b9614a0feab70dd97cfd64861737c8b42dd146b7
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248033"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associare un'area del modulo a una classe messaggio di Outlook
  È possibile specificare quali elementi di Microsoft Office Outlook visualizzano un'area del modulo associando l'area del modulo con la classe messaggio di ogni elemento. Ad esempio, se si desidera aggiungere un'area del modulo nella parte inferiore di un elemento di posta elettronica, è possibile associare l'area del modulo con il `IPM.Note` classe message.  
  
 Per associare un'area del modulo a una classe messaggio, specificare il nome della classe messaggio nel **nuova area del modulo Outlook** guidata o applicare un attributo alla classe factory area del modulo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understand-outlook-message-classes"></a>Comprendere le classi di messaggi di Outlook  
 Una classe messaggio di Outlook identifica un tipo di elemento di Outlook. La tabella seguente elenca questi otto tipi standard di elementi e i relativi nomi di classe messaggio.  
  
|Tipo di elemento di Outlook|Nome della classe messaggio|  
|-----------------------|------------------------|  
|Oggetto AppointmentItem|`IPM.Appointment`|  
|ContactItem|`IPM.Contact`|  
|DistListItem|`IPM.DistList`|  
|JournalItem|`IPM.Activity`|  
|Oggetto MailItem|`IPM.Note`|  
|PostItem|`IPM.Post` o `IPM.Post.RSS`|  
|TaskItem|`IPM.Task`|  
  
 È anche possibile specificare i nomi delle classi messaggio personalizzate. Classi messaggio personalizzate identificano i moduli personalizzati definiti in Outlook.  
  
> [!NOTE]  
>  Per aree del modulo di sostituzione e sostituzione, è possibile specificare un nuovo nome della classe messaggio personalizzata. Non devi usare il nome della classe messaggio di un modulo personalizzato esistente. Il nome della classe messaggio personalizzata deve essere univoco. Un modo per assicurarsi che il nome sia univoco è usare una convenzione di denominazione simile al seguente: \<*StandardMessageClassName*>.\< *Società*>.\< *MessageClassName*> (ad esempio: `IPM.Note.Contoso.MyMessageClass`).  
  
## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associare un'area del modulo a una classe messaggio di Outlook  
 Esistono due modi per associare un'area del modulo a una classe messaggio:  
  
-   Usare la **nuova area del modulo Outlook** procedura guidata.  
  
-   Applicare gli attributi di classe.  
  
### <a name="use-the-new-outlook-form-region-wizard"></a>Utilizzare la procedura guidata nuova area del modulo di Outlook  
 Nella pagina finale della **nuova area del modulo Outlook** procedura guidata, è possibile selezionare le classi messaggio standard e digitare i nomi delle classi messaggio personalizzate che si desidera associare l'area del modulo.  
  
 Le classi messaggio standard non sono disponibili se l'area del modulo è progettato per sostituire l'intero form o la pagina predefinita di un form. È possibile specificare i nomi delle classi messaggio standard solo per i moduli che consentono di aggiungere una nuova pagina a un form o che vengono aggiunti alla parte inferiore della forma. Per altre informazioni, vedere [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Per includere uno o più classi messaggio personalizzate, digitare i nomi nella **le classi messaggio personalizzate che visualizzerà l'area del modulo?** casella.  
  
 I nomi digitati devono essere conformi alle linee guida seguenti:  
  
- Usare il nome della classe messaggio completo (ad esempio: "IPM. Contoso").  
  
- Usare un punto e virgola per separare più nomi di classe messaggio.  
  
- Non includere classi di messaggio standard di Outlook, ad esempio "IPM. Si noti"o"IPM. Contact". Includere solo le classi messaggio personalizzate, ad esempio "IPM. Contoso".  
  
- Non si specifica la classe di messaggi di base da solo (ad esempio: "IPM").  
  
- Non superare i 256 caratteri per ogni nome di classe messaggio.  
  
  Il **nuova area del modulo di Outlook** procedura guidata convalida il formato dell'input quando si fa clic **fine**.  
  
> [!NOTE]  
>  Il **nuova area del modulo Outlook** guidata non verifica che i nomi di classe messaggio specificata dall'utente siano corretti o valido.  
  
 Quando si completa la procedura guidata, il **nuova area del modulo Outlook** Applica attributi alla classe di area del modulo che contiene i nomi delle classi messaggio specificato. È anche possibile applicare manualmente tali attributi.  
  
### <a name="apply-class-attributes"></a>Applicare gli attributi della classe  
 È possibile associare un'area del modulo con una classe messaggio di Outlook, dopo aver completato la **nuova area del modulo Outlook** procedura guidata. A tale scopo, applicare gli attributi per la classe factory area del modulo.  
  
 Nell'esempio seguente vengono illustrati due <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> gli attributi che sono stati applicati a una classe factory dell'area modulo denominata `myFormRegion`. Il primo attributo associa l'area del modulo con una classe di messaggio standard per un modulo di messaggio di posta elettronica. Il secondo attributo associa l'area del modulo a una classe messaggio personalizzata denominata `IPM.Task.Contoso`.  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 Gli attributi devono essere conformi alle linee guida seguenti:  
  
- Per le classi messaggio personalizzate, usare il nome della classe messaggio completo (ad esempio: "IPM. Contoso").  
  
- Non si specifica la classe di messaggi di base da solo (ad esempio: "IPM").  
  
- Non superare i 256 caratteri per ogni nome di classe messaggio.  
  
- Se l'area del modulo sostituisce l'intero form o la pagina predefinita di un modulo non includono i nomi delle classi messaggio standard. È possibile specificare i nomi delle classi messaggio standard solo per i moduli che consentono di aggiungere una nuova pagina a un form o che vengono aggiunti alla parte inferiore della forma. Per altre informazioni, vedere [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
  Visual Studio convalida il formato dei nomi di classe messaggio quando si compila il progetto.  
  
> [!NOTE]  
>  Visual Studio non verifica che i nomi di classe messaggio specificata dall'utente siano corretti o valido.  
  
## <a name="see-also"></a>Vedere anche  
 [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)   
 [Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura dettagliata: Progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Linee guida per creare aree del modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Nome del modulo e classi messaggio Panoramica](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)   
 [Interagiscono tra gli elementi e i moduli di Outlook](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)  
  
  