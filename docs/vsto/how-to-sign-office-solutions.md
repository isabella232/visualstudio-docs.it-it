---
title: 'Procedura: firmare soluzioni Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d5fa4a837de66a39502e2c9e2d8466f3998acc4d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262191"
---
# <a name="how-to-sign-office-solutions"></a>Procedura: firmare soluzioni Office
  Se si firma una soluzione, è possibile concedere l'attendibilità alla soluzione mediante il certificato come prova. È possibile utilizzare lo stesso certificato per più soluzioni e tutte le soluzioni saranno attendibili senza aggiornamenti di criteri di sicurezza aggiuntiva.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se si modifica manualmente applicazione e i manifesti della distribuzione tramite la generazione e la modifica dello strumento (*mage.exe* e *mageui.exe*), è necessario firmare nuovamente i manifesti prima di utilizzarli. Per altre informazioni, vedere [procedura: firmare manifesti dell'applicazione e distribuzione](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="sign-by-using-a-certificate"></a>Accedere utilizzando un certificato  
 Un certificato è un file che contiene una chiave univoca e l'identità del server di pubblicazione di soluzioni. È possibile acquistare certificati da un'autorità di certificazione o creare un certificato personalizzato e un'autorità di certificazione firmarlo.  
  
 Visual Studio firma con un certificato temporaneo per abilitare il debug di soluzioni Office. Non utilizzare il certificato temporaneo nelle soluzioni distribuite come evidenza.  
  
### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Per accedere a una soluzione Office usando un certificato  
  
1.  Nel **Project** menu, fare clic su * SolutionName ***proprietà**.  
  
2.  Fare clic sulla scheda **Firma**.  
  
3.  Selezionare **firmare i manifesti ClickOnce**.  
  
4.  Individuare il certificato, fare clic su **seleziona da archivio** o **seleziona da File** e passare al certificato.  
  
5.  Per verificare che venga utilizzato il certificato corretto, fare clic su **più dettagli** per visualizzare le informazioni sul certificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)   
 [Concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)   
 [Pagina Firma, Creazione progetti](/visualstudio/ide/reference/signing-page-project-designer)  
  
  