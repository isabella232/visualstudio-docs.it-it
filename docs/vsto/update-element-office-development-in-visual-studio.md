---
title: '&lt;Elemento &gt; update (Office sviluppo in Visual Studio)'
description: L'elemento update specifica l'intervallo in base al quale la soluzione verifica la disponibilità di aggiornamenti.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 35f082a176c958ea40539fac594f1119405de819b7ab054f4c51010aff2044a3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121365926"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Elemento &gt; update (Office sviluppo in Visual Studio)
  `update`L'elemento specifica l'intervallo in base al quale la soluzione verifica la disponibilità di aggiornamenti.

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
|`enabled`|Obbligatorio. Impostare enabled su uno dei valori seguenti:<br /><br /> -   **true per** verificare la disponibilità di aggiornamenti.<br />-   **false per** impedire il controllo degli aggiornamenti.|

 L'elemento `update` ha gli elementi figlio seguenti.

### <a name="expiration"></a>expiration
 L'elemento `expiration` è obbligatorio e si trova nello spazio dei nomi `vstav3` . Questo elemento specifica l'intervallo in base al quale la soluzione verifica la disponibilità di aggiornamenti.

 L'elemento `expiration` presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`maximumAge`| Obbligatorio. Impostare questa proprietà su un numero intero.|
|`unit`|Obbligatorio. Impostare `unit` su uno dei valori seguenti:<br /><br /> -   **Ore**<br />-   **Giorni**<br />-   **Settimane**|

## <a name="example-of-always-checking-for-updates"></a>Esempio di controllo sempre della disponibilità di aggiornamenti

### <a name="description"></a>Descrizione
 Nell'esempio di codice seguente viene illustrato un elemento impostato per verificare sempre la disponibilità di `update` aggiornamenti Office soluzioni.

### <a name="code"></a>Codice

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Esempio di impostazione di un intervallo di aggiornamento predefinito

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra un `update` elemento in un manifesto dell'applicazione per Office soluzioni. Questo esempio di codice fa parte di un esempio più ampio fornito in [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Vedi anche

- [Distribuire una Office di distribuzione usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
