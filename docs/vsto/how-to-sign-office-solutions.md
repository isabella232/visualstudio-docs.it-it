---
title: 'Procedura: firmare soluzioni Office'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 23afc171fd97620b3e6801b8d199da6890198d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545756"
---
# <a name="how-to-sign-office-solutions"></a>Procedura: firmare soluzioni Office
  Se si firma una soluzione, è possibile concedere l'attendibilità alla soluzione usando il certificato come evidenza. È possibile utilizzare lo stesso certificato per più soluzioni e tutte le soluzioni verranno considerate attendibili senza ulteriori aggiornamenti dei criteri di sicurezza.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Se si modificano manualmente i manifesti dell'applicazione e della distribuzione usando il Strumento per la generazione e la modifica di manifesti (*mage.exe* e *mageui.exe*), è necessario firmare di nuovo i manifesti prima di poterli usare. Per altre informazioni, vedere [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Firma tramite un certificato
 Un certificato è un file che contiene una chiave univoca e l'identità del server di pubblicazione della soluzione. È possibile acquistare certificati da un'autorità di certificazione o creare un certificato personalizzato e firmarlo da un'autorità di certificazione.

 Visual Studio firma le soluzioni Office con un certificato temporaneo per abilitare il debug. Non usare il certificato temporaneo nelle soluzioni distribuite come prova.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Per firmare una soluzione Office usando un certificato

1. Scegliere**proprietà** _SolutionName_dal menu **progetto** .

2. Fare clic sulla scheda **Firma** .

3. Selezionare **firma i manifesti ClickOnce**.

4. Individuare il certificato facendo clic su **Seleziona dall'archivio** o **Seleziona da file** e passando al certificato.

5. Per verificare che sia in uso il certificato corretto, fare clic su **altri dettagli** per visualizzare le informazioni sul certificato.

## <a name="see-also"></a>Vedere anche

- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Concedi attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)
- [Pagina Firma, Progettazione progetti](../ide/reference/signing-page-project-designer.md)
