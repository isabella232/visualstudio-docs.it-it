---
title: VSPerfASPNetCmd | Microsoft Docs
description: Informazioni su come lo VSPerfASPNetCmd.exe da riga di comando consente di profilare ASP.Net siti Web senza richiedere l'impostazione di variabili di ambiente o il riavvio del computer.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0a496c0ab434ed115e28d88874e4fdbc64931f89
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156773"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
Lo strumento da riga di comando **VSPerfASPNetCmd.exe** consente di profilare i siti Web ASP.Net senza la necessità di impostare le variabili di ambiente o di riavviare il computer. Usare **VSPerfASPNetCmd.exe** anziché [VSPerfCmd](../profiling/vsperfcmd.md) quando si esegue la profilatura dei siti Web ASP.NET e non è necessaria la funzionalità aggiuntiva fornita da **VSPerfCmd**. Per altre informazioni su **VSPerfASPNetCmd,** vedere Profilatura rapida del sito [Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNetCmd** è lo strumento da riga di comando preferito da usare quando si usa il profiler autonomo per profilare un sito Web ASP.NET.

## <a name="syntax"></a>Sintassi
 **vsperfaspnetcmd** [*/Options*] *Website*

## <a name="options"></a>Opzioni

|Opzione|Descrizione|
|------------|-----------------|
|**/Sample** o **/s**|Esegue la profilatura del sito Web tramite il metodo di campionamento. **/Sample** è il metodo predefinito. /Sample non può essere usato con **/Trace**.|
|**/Trace** o **/t**|Sottoporre a profilatura il sito Web tramite il metodo di strumentazione. /Trace non può essere usato con **/Sample**.|
|**/Memory**[**:** `Type` ]o **/m**[**:**{**a&#124;** **l**}]|I profili di allocazione della memoria e, facoltativamente, i profili della durata degli oggetti (garbage collection). **/Memory** può essere usato con il metodo di campionamento o di strumentazione.<br /><br /> *Tipo* può essere uno dei seguenti:<br /><br /> -   **allocazione** (o **a**) raccoglie solo i dati sull'allocazione della memoria.<br />-   **durata** (o **l**) raccoglie i dati sull'allocazione della memoria e quelli sulla durata dell'oggetto.<br /><br /> Il valore predefinito `Type` è **allocazione**.|
|**/Tip** o   **/i**|Aggiunge una richiesta ASP.NET dettagliata e informazioni sulla chiamata ADO.NET ai dati relativi alla profilatura. **/ Tip** può essere usato con il metodo campionamento o di strumentazione e può essere usato con l'opzione **/Memory**.|
|**/ Output:** `File` o **/o:**`File`|Specifica il percorso e il nome file dei dati di profilatura (.*vsp*) file.|
|**/NoWait** o   **/n**|Restituisce il prompt dei comandi immediatamente in modo che i comandi aggiuntivi possano essere usati nella finestra del prompt dei comandi. È necessario digitare **VSPerfASPNETCmd /Shutdown** su una riga di comando separata per disattivare la profilatura.|
|**/PackSymbols**[:{**on**&#124;**off**}o   **/p**[:{**on**&#124;**off**}|Incorpora simboli (nomi di funzione e di parametro e così via) nel file dei dati di profilatura (con estensione *vsp*).|
|**/Shutdown:** `Website` o   **/d:**`Website`|Disattiva la profilatura. Usare come unica opzione in una riga di comando dopo aver usato l'opzione **/NoWait** per avviare la profilatura, o se il profiler termina in modo imprevisto. Specificare lo stesso url usato nel comando originale **VSPerfASPNETCmd**.|
|`Website`|L'url del sito Web da profilare.|

## <a name="see-also"></a>Vedi anche
- [Profilatura rapida del sito Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
