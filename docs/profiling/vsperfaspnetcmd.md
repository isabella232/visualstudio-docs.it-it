---
title: VSPerfASPNetCmd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b6ddadc15a5e0d53535b82d87aadd31fec65adaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330475"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
Lo strumento da riga di comando **VSPerfASPNetCmd.exe** consente di profilare i siti Web ASP.Net senza la necessità di impostare le variabili di ambiente o di riavviare il computer. Usare **VSPerfASPNetCmd.exe** anziché [VSPerfCmd](../profiling/vsperfcmd.md) quando si esegue la profilatura dei siti Web ASP.NET e non è necessaria la funzionalità aggiuntiva fornita da **VSPerfCmd**. Per ulteriori informazioni su **VSPerfASPNetCmd**, vedere [profilatura rapida di siti Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNetCmd** è lo strumento da riga di comando preferito da usare quando si usa il profiler autonomo per profilare un sito Web ASP.NET.

## <a name="syntax"></a>Sintassi
 **vsperfaspnetcmd** [*/Options*] *Website*

## <a name="options"></a>Opzioni

|Opzione|Descrizione|
|------------|-----------------|
|**/Sample** o **/s**|Esegue la profilatura del sito Web tramite il metodo di campionamento. **/Sample** è il metodo predefinito. /Sample non può essere usato con **/Trace**.|
|**/Trace** o **/t**|Sottoporre a profilatura il sito Web tramite il metodo di strumentazione. /Trace non può essere usato con **/Sample**.|
|**/Memory**[**:** `Type` ] o **/m**[**:**{**a**&#124;**l**}]|I profili di allocazione della memoria e, facoltativamente, i profili della durata degli oggetti (garbage collection). **/Memory** può essere usato con il metodo di campionamento o di strumentazione.<br /><br /> *Tipo* può essere uno dei seguenti:<br /><br /> -   **allocazione** (o **a**) raccoglie solo i dati sull'allocazione della memoria.<br />-   **durata** (o **l**) raccoglie i dati sull'allocazione della memoria e quelli sulla durata dell'oggetto.<br /><br /> Il valore predefinito `Type` è **allocazione**.|
|**/Tip** o   **/i**|Aggiunge una richiesta ASP.NET dettagliata e informazioni sulla chiamata ADO.NET ai dati relativi alla profilatura. **/ Tip** può essere usato con il metodo campionamento o di strumentazione e può essere usato con l'opzione **/Memory**.|
|**/ Output:** `File` o **/o:**`File`|Specifica il percorso e il nome file dei dati di profilatura (.* VSP*).|
|**/NoWait** o   **/n**|Restituisce il prompt dei comandi immediatamente in modo che i comandi aggiuntivi possano essere usati nella finestra del prompt dei comandi. È necessario digitare **VSPerfASPNETCmd /Shutdown** su una riga di comando separata per disattivare la profilatura.|
|**/PackSymbols**[:{**on**&#124;**off**}o   **/p**[:{**on**&#124;**off**}|Incorpora simboli (nomi di funzione e di parametro e così via) nel file dei dati di profilatura (con estensione *vsp*).|
|**/Shutdown:** `Website`o   **/d:**`Website`|Disattiva la profilatura. Usare come unica opzione in una riga di comando dopo aver usato l'opzione **/NoWait** per avviare la profilatura, o se il profiler termina in modo imprevisto. Specificare lo stesso url usato nel comando originale **VSPerfASPNETCmd**.|
|`Website`|L'url del sito Web da profilare.|

## <a name="see-also"></a>Vedere anche
- [Profilatura rapida di siti Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
