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
ms.openlocfilehash: 161c175b6bb37ece93559f0378bbaf8e5e16d170
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776133"
---
# <a name="how-to-sign-office-solutions"></a>Procedura: firmare soluzioni Office
  Se si accede a una soluzione, è possibile concedere l'attendibilità alla soluzione usando il certificato come evidenza. È possibile usare lo stesso certificato per più soluzioni, e tutte le soluzioni saranno attendibili senza aggiornamenti dei criteri di sicurezza aggiuntive.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se si modifica manualmente l'applicazione e manifesti della distribuzione tramite il Manifest Generation and Editing Tool (*mage.exe* e *mageui.exe*), è necessario firmare nuovamente i manifesti prima di usarli. Per altre informazioni, vedere [procedura: firmare manifesti dell'applicazione e distribuzione](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="sign-by-using-a-certificate"></a>Accedere usando un certificato  
 Un certificato è un file che contiene una chiave univoca e l'identità dell'autore di soluzioni. È possibile acquistare i certificati da un'autorità di certificazione, o creare un certificato e un'autorità di certificazione firmarlo.  
  
 Visual Studio esegue l'accesso con un certificato temporaneo per abilitare il debug di soluzioni Office. Non utilizzare il certificato temporaneo generato in soluzioni distribuite come evidenza.  
  
### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Per firmare una soluzione Office usando un certificato  
  
1.  Nel **progetto** menu, fare clic su _NomeSoluzione_**proprietà**.  
  
2.  Fare clic sulla scheda **Firma**.  
  
3.  Selezionare **firmare i manifesti ClickOnce**.  
  
4.  Individuare il certificato facendo **Store, selezionarne** oppure **seleziona da File** e passare al certificato.  
  
5.  Per verificare che il certificato corretto sia in uso, fare clic su **altri dettagli sul** per visualizzare le informazioni del certificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)   
 [Concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)   
 [Pagina Firma, Creazione progetti](/visualstudio/ide/reference/signing-page-project-designer)  
  
  