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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d6f48be189b7d7a35f713c224553dc9ad7c8a5c3
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268230"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associare un'area del modulo a una classe messaggio di Outlook
  È possibile specificare quali elementi di Microsoft Office Outlook visualizzano un'area del modulo associando l'area del modulo con la classe messaggio di ogni elemento. Ad esempio, se si desidera aggiungere un'area del modulo alla fine di un elemento di posta elettronica, è possibile associare l'area del modulo con il `IPM.Note` classe message.  
  
 Per associare un'area del modulo a una classe di messaggio, specificare il nome della classe nel messaggio il **nuova area del modulo di Outlook** procedura guidata o applicare un attributo a una classe factory area del modulo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understand-outlook-message-classes"></a>Comprendere le classi di messaggio di Outlook  
 Una classe messaggio di Outlook identifica un tipo di elemento di Outlook. Nella tabella seguente sono elencati questi otto tipi standard di elementi e i nomi di classe di messaggio.  
  
|Tipo di elemento di Outlook|Nome della classe messaggio|  
|-----------------------|------------------------|  
|Oggetto AppointmentItem|`IPM.Appointment`|  
|Oggetto ContactItem|`IPM.Contact`|  
|DistListItem|`IPM.DistList`|  
|JournalItem|`IPM.Activity`|  
|Oggetto MailItem|`IPM.Note`|  
|PostItem|`IPM.Post` o `IPM.Post.RSS`|  
|Oggetto TaskItem|`IPM.Task`|  
  
 È inoltre possibile specificare i nomi delle classi messaggio personalizzate. Classi messaggio personalizzate identificano i moduli personalizzati definiti in Outlook.  
  
> [!NOTE]  
>  Per la sostituzione e aree del modulo di sostituzione completa, è possibile specificare un nuovo nome di classe messaggio personalizzata. Non è necessario utilizzare il nome della classe messaggio di un modulo personalizzato esistente. Il nome della classe messaggio personalizzata deve essere univoco. Un modo per garantire che il nome sia univoco consiste nell'utilizzare una convenzione di denominazione simile al seguente: \< *StandardMessageClassName*>.\< *Società*>.\< *MessageClassName*> (ad esempio: `IPM.Note.Contoso.MyMessageClass`).  
  
## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associare un'area del modulo a una classe messaggio di Outlook  
 Esistono due modi per associare un'area del modulo a una classe messaggio:  
  
-   Utilizzare il **nuova area del modulo di Outlook** procedura guidata.  
  
-   Applicare gli attributi di classe.  
  
### <a name="use-the-new-outlook-form-region-wizard"></a>Utilizzare la procedura guidata nuova area del modulo di Outlook  
 Nella pagina finale del **nuova area del modulo di Outlook** procedura guidata, è possibile selezionare le classi messaggio standard e digitare i nomi delle classi di messaggi personalizzato che si desidera associare l'area del modulo.  
  
 Le classi messaggio standard non sono disponibili se l'area del modulo è progettata per sostituire l'intero modulo o la pagina predefinita di un form. È possibile specificare i nomi delle classi messaggio standard solo per i moduli che consentono di aggiungere una nuova pagina a un form o che vengono aggiunti alla fine di un modulo. Per altre informazioni, vedere [procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Per includere uno o più classi messaggio personalizzate, digitare i nomi nella **le classi di messaggi visualizzerà l'area del modulo?** casella.  
  
 I nomi digitati devono rispettare le linee guida seguenti:  
  
-   Utilizzare il nome della classe messaggio completo (ad esempio: "IPM. Contoso").  
  
-   Utilizzare un punto e virgola per separare più nomi di classe di messaggio.  
  
-   Non includere classi di messaggio standard di Outlook, ad esempio "IPM. Nota"o"IPM. Contatto". Includere solo le classi di messaggi, ad esempio "IPM. Contoso".  
  
-   Non si specifica la classe messaggio di base da solo (ad esempio: "IPM").  
  
-   Non superare 256 caratteri per il nome di ogni classe di messaggio.  
  
 Il **nuova area del modulo di Outlook** procedura guidata convalida il formato dell'input quando si fa clic su **fine**.  
  
> [!NOTE]  
>  Il **nuova area del modulo di Outlook** guidata verifica che i nomi delle classi messaggio forniti siano corretti o validi.  
  
 Quando si completa la procedura guidata, il **nuova area del modulo di Outlook** applica gli attributi alla classe di area del modulo che contiene i nomi di classe di messaggio specificato. È inoltre possibile applicare questi attributi manualmente.  
  
### <a name="apply-class-attributes"></a>Applicare gli attributi della classe  
 È possibile associare un'area del modulo a una classe messaggio di Outlook, dopo aver completato il **nuova area del modulo di Outlook** procedura guidata. A tale scopo, applicare gli attributi per la classe factory area del modulo.  
  
 Nell'esempio seguente vengono illustrati due <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> attributi applicati a una classe factory dell'area modulo denominata `myFormRegion`. Il primo attributo associa l'area del modulo con una classe di messaggio standard per un modulo di messaggio di posta elettronica. Il secondo attributo associa l'area del modulo a una classe messaggio personalizzata denominata `IPM.Task.Contoso`.  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 Gli attributi devono rispettare le linee guida seguenti:  
  
-   Per le classi di messaggi personalizzato, utilizzare il nome della classe messaggio completo (ad esempio: "IPM. Contoso").  
  
-   Non si specifica la classe messaggio di base da solo (ad esempio: "IPM").  
  
-   Non superare 256 caratteri per il nome di ogni classe di messaggio.  
  
-   Non includere i nomi delle classi messaggio standard se l'area del modulo sostituisce l'intero modulo o la pagina predefinita di un form. È possibile specificare i nomi delle classi messaggio standard solo per i moduli che consentono di aggiungere una nuova pagina a un form o che vengono aggiunti alla fine di un modulo. Per altre informazioni, vedere [procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Quando si compila il progetto, Visual Studio convalida il formato dei nomi di classe di messaggio.  
  
> [!NOTE]  
>  Visual Studio non verifica che i nomi delle classi messaggio forniti siano corretti o validi.  
  
## <a name="see-also"></a>Vedere anche  
 [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)   
 [Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura dettagliata: Progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Linee guida per creare aree del modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Panoramica della classe Form name e message](http://msdn.microsoft.com/library/office/ff867629.aspx)   
 [Interagiscono tra gli elementi e i moduli di Outlook](http://msdn.microsoft.com/library/office/ff869706.aspx)  
  
  