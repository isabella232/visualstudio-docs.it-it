---
title: 'Procedura: Specificare l''icona di un''applicazione (Visual Basic, C#) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: ce92aef6f676cbdd35142f058312af90581900c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Procedura: specificare l'icona di un'applicazione (Visual Basic, C#)
La proprietà `Icon` per un progetto specifica il file icona (.ico) che verrà visualizzato per l'applicazione compilata in Esplora file e nella barra delle applicazioni di Windows.  
  
 È possibile accedere alla proprietà `Icon` nel riquadro **Applicazione** di **Creazione progetti**. Contiene un elenco delle icone aggiunte a un progetto come risorse o come file di contenuto.  
  
> [!NOTE]
>  Dopo aver impostato la proprietà dell'icona per un'applicazione, è anche possibile impostare la proprietà `Icon` di ogni **Finestra** o **Modulo** nell'applicazione. Per informazioni sulle icone della finestra per applicazioni autonome WPF (Windows Presentation Foundation), vedere la proprietà <xref:System.Windows.Window.Icon%2A>.  
  
### <a name="to-specify-an-application-icon"></a>Per specificare l'icona di un'applicazione  
  
1.  In **Esplora soluzioni** scegliere un nodo progetto, non il nodo **Soluzione**.  
  
2.  Sulla barra dei menu scegliere **Progetto**, **Proprietà**.  
  
3.  Quando si apre **Creazione progetti**, scegliere la scheda **Applicazione**.  
  
4.  **(Visual Basic)** Nell'elenco **Icona** scegliere un file icona con estensione ico.  
  
     **C#** Accanto all'elenco **Icona** scegliere il pulsante **\<Sfoglia** e selezionare il percorso del file icona desiderato.  
  
## <a name="see-also"></a>Vedere anche  
 [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  (Pagina Applicazione, Creazione progetti (Visual Basic))  
 [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)  (Applicazione (pagina), Creazione progetti (C#))  
 [Managing Application Properties](../ide/application-properties.md)(Gestione delle proprietà delle applicazioni)  
 [Procedura: Aggiungere o rimuovere risorse](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)