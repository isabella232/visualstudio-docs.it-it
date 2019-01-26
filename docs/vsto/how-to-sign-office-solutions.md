---
title: 'Procedura: Firmare soluzioni Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25c5388c1b1d14efad9e76b2494f8da423d28979
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871663"
---
# <a name="how-to-sign-office-solutions"></a>Procedura: Firmare soluzioni Office
  Se si accede a una soluzione, è possibile concedere l'attendibilità alla soluzione usando il certificato come evidenza. È possibile usare lo stesso certificato per più soluzioni, e tutte le soluzioni saranno attendibili senza aggiornamenti dei criteri di sicurezza aggiuntive.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Se si modifica manualmente l'applicazione e manifesti della distribuzione tramite il Manifest Generation and Editing Tool (*mage.exe* e *mageui.exe*), è necessario firmare nuovamente i manifesti prima di usarli. Per altre informazioni, vedere [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

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

- [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)
- [Concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)
- [Pagina Firma, Creazione progetti](../ide/reference/signing-page-project-designer.md)
