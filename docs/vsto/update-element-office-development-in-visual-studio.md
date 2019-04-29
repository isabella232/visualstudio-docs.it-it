---
title: '&lt;aggiornare&gt; elemento (sviluppo per Office in Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 461fae79e3af346d64017166b6dae3ace67599e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967533"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;aggiornare&gt; elemento (sviluppo per Office in Visual Studio)
  Il `update` elemento specifica l'intervallo in corrispondenza del quale la soluzione controllerà gli aggiornamenti.

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
|`enabled`|Obbligatorio. Impostare enabled su uno dei valori seguenti:<br /><br /> -   **true** per cercare gli aggiornamenti.<br />-   **false** per impedire il controllo degli aggiornamenti.|

 L'elemento `update` ha gli elementi figlio seguenti.

### <a name="expiration"></a>scadenza
 L'elemento `expiration` è obbligatorio e si trova nello spazio dei nomi `vstav3` . Questo elemento specifica l'intervallo in corrispondenza del quale la soluzione Controlla disponibilità di aggiornamenti.

 L'elemento `expiration` presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`maximumAge`| Obbligatorio. Impostare su un numero intero.|
|`unit`|Obbligatorio. Impostare `unit` a uno dei valori seguenti:<br /><br /> -   **Ore**<br />-   **Giorni**<br />-   **Settimane**|

## <a name="example-of-always-checking-for-updates"></a>Ad esempio sempre il controllo degli aggiornamenti

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra un `update` elemento sul quale è impostata per verificare sempre gli aggiornamenti nelle soluzioni Office.

### <a name="code"></a>Codice

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Esempio di impostazione di un intervallo di aggiornamento predefinito

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra un `update` elemento in un manifesto dell'applicazione per le soluzioni Office. Questo esempio di codice è parte di un esempio più esaustivo disponibile nel [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Vedere anche

- [Distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
