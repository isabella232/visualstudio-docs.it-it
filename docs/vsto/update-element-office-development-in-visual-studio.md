---
title: '&lt;&gt;elemento Update (sviluppo per Office in Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241bddb8c79a01bb1ba6921486a4dc46d99940cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537384"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento Update (sviluppo per Office in Visual Studio)
  L' `update` elemento specifica l'intervallo in corrispondenza del quale la soluzione verificherà la disponibilità di aggiornamenti.

## <a name="syntax"></a>Sintassi

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `update` è obbligatorio e si trova nello spazio dei nomi `vstav3` .

 L'elemento `update` presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`enabled`|Obbligatorio. Impostare abilitato su uno dei valori seguenti:<br /><br /> -   **true** per verificare la disponibilità di aggiornamenti.<br />-   **false** per impedire il controllo degli aggiornamenti.|

 L'elemento `update` ha gli elementi figlio seguenti.

### <a name="expiration"></a>expiration
 L'elemento `expiration` è obbligatorio e si trova nello spazio dei nomi `vstav3` . Questo elemento specifica l'intervallo con cui la soluzione controlla la disponibilità di aggiornamenti.

 L'elemento `expiration` presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`maximumAge`| Obbligatorio. Impostare questa impostazione su un valore integer.|
|`unit`|Obbligatorio. Impostare `unit` su uno dei valori seguenti:<br /><br /> -   **ore**<br />-   **giorni**<br />-   **settimane**|

## <a name="example-of-always-checking-for-updates"></a>Esempio di controllo continuo della disponibilità di aggiornamenti

### <a name="description"></a>Descrizione
 Nell'esempio di codice seguente viene illustrato un `update` elemento che è impostato per verificare sempre la presenza di aggiornamenti nelle soluzioni Office.

### <a name="code"></a>Codice

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Esempio di impostazione di un intervallo di aggiornamento predefinito

### <a name="description"></a>Descrizione
 Nell'esempio di codice seguente viene illustrato un `update` elemento in un manifesto dell'applicazione per le soluzioni Office. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Vedere anche

- [Distribuire una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
