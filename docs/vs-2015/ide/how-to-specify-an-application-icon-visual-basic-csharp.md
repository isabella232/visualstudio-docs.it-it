---
title: "Procedura: Specificare un'icona dell'applicazione (Visual Basic, C#) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f794f1c988215f8899dce495f725b3a9c14a435
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788165"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Procedura: specificare l'icona di un'applicazione (Visual Basic, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Procedura: Aggiungere o rimuovere risorse](http://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
