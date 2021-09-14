---
title: 'Procedura: Firmare Office soluzioni'
description: Informazioni su come concedere l'attendibilità alla soluzione Microsoft Office usando un certificato come evidenza.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ab1fa5de20975b3c08d95906cef1288ebe8f4ec5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711319"
---
# <a name="how-to-sign-office-solutions"></a>Procedura: Firmare Office soluzioni
  Se si firma una soluzione, è possibile concedere l'attendibilità alla soluzione usando il certificato come evidenza. È possibile usare lo stesso certificato per più soluzioni e tutte le soluzioni saranno attendibili senza aggiornamenti dei criteri di sicurezza aggiuntivi.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Se si modificano manualmente i manifesti dell'applicazione e della distribuzione usando il Strumento per la generazione e la modifica di manifesti (*mage.exe* e *mageui.exe*), è necessario firmare nuovamente i manifesti prima di poterli usare. Per altre informazioni, vedere [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Firmare con un certificato
 Un certificato è un file che contiene una chiave univoca e l'identità dell'autore della soluzione. È possibile acquistare certificati da un'autorità di certificazione o creare un certificato personalizzato e fare in modo che un'autorità di certificazione lo firma.

 Visual Studio firma Office soluzioni con un certificato temporaneo per abilitare il debug. È consigliabile non usare il certificato temporaneo nelle soluzioni distribuite come prova.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Per firmare una Office usando un certificato

1. Nel menu **Project** fare clic su _Proprietà NomeSo soluzioni_**.**

2. Fare clic sulla scheda **Firma** .

3. Selezionare **Firma ClickOnce manifesti.**

4. Individuare il certificato facendo **clic su Seleziona dall'archivio** o Seleziona da **file** e passando al certificato.

5. Per verificare che venga usato il certificato corretto, fare clic su **Altri dettagli** per visualizzare le informazioni sul certificato.

## <a name="see-also"></a>Vedi anche

- [Proteggere Office soluzioni](../vsto/securing-office-solutions.md)
- [Concedere l'attendibilità Office soluzioni](../vsto/granting-trust-to-office-solutions.md)
- [Pagina Firma, Progettazione progetti](../ide/reference/signing-page-project-designer.md)
