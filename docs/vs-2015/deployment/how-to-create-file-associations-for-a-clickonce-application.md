---
title: "Procedura: creare associazioni di file per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82ffecdc719dad2f38208de00dc95438b3ff36ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697695"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Procedura: creare associazioni di file per un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le applicazioni possono essere associate a una o più estensioni di file, in modo che l'applicazione venga avviata automaticamente quando l'utente apre un file di tali tipi. L'aggiunta del supporto dell'estensione del nome di file a un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione è semplice.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Per creare associazioni di file per un'applicazione ClickOnce  
  
1. Creare un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione normalmente oppure usare l'applicazione esistente [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
2. Aprire il manifesto dell'applicazione con un editor di testo o XML, ad esempio Blocco note.  
  
3. Trovare l'elemento `assembly`. Per altre informazioni, vedere [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4. `assembly`Aggiungere un elemento come figlio dell'elemento `fileAssociation` . L' `fileAssociation` elemento ha quattro attributi:  
  
   - `extension`: Estensione del nome di file che si desidera associare all'applicazione.  
  
   - `description`: Descrizione del tipo di file, che verrà visualizzato nella shell di Windows.  
  
   - `progid`: Stringa che identifica in modo univoco il tipo di file, per contrassegnarla nel registro di sistema.  
  
   - `defaultIcon`: Icona da usare per questo tipo di file. L'icona deve essere aggiunta come risorsa file nel manifesto dell'applicazione. Per altre informazioni, vedere [procedura: includere un file di dati in un'applicazione ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Per un esempio degli `file` elementi e `fileAssociation` , vedere [ \<fileAssociation> elemento](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Se si desidera associare più di un tipo di file all'applicazione, aggiungere altri `fileAssociation` elementi. Si noti che l' `progid` attributo deve essere diverso per ogni.  
  
6. Una volta terminato il manifesto dell'applicazione, firmare nuovamente il manifesto. È possibile eseguire questa operazione dalla riga di comando utilizzando Mage.exe.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Per ulteriori informazioni, vedere [Mage.exe (strumento per la generazione e la modifica di manifesti)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>Vedere anche  
 [\<fileAssociation> Elemento](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
