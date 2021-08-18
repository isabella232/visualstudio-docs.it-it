---
title: Profilatura rapida di sito Web con VSPerfASPNETCmd | Microsoft Docs
description: Informazioni su come lo strumento da riga di comando VSPerfASPNETCmd consente di profilare facilmente ASP.NET applicazioni Web.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: af271772104d1e21f211987c8dcee54fdf0a88c3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141571"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Profilatura rapida di sito Web con VSPerfASPNETCmd

Lo strumento da riga di comando **VSPerfASPNETCmd** consente di profilare facilmente [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] le applicazioni Web. Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), le opzioni sono ridotte, non è necessario impostare variabili di ambiente e non è richiesto il riavvio del computer. **VSPerfASPNETCmd** è il metodo preferito per la profilatura con il profiler autonomo. Per altre informazioni, vedere [Procedura: Installare il profiler autonomo](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni Windows 8 e Windows Server 2012 applicazioni](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 In alcuni scenari, quali la raccolta di dati di concorrenza o la sospensione e la ripresa della profilatura, **VSPerfCmd** costituisce il metodo di profilatura preferito.

> [!NOTE]
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

## <a name="profile-an-aspnet-application"></a>Profiling di un'applicazione ASP.NET

Per profilare un'applicazione Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], digitare uno dei comandi descritti nelle sezioni seguenti. Il sito Web viene avviato e il profiler inizia a raccogliere dati. Verificare la funzionalità dell'applicazione e quindi chiudere il browser. Per interrompere la profilatura, premere **INVIO** nella finestra del prompt dei comandi.

> [!NOTE]
> Per impostazione predefinita, il prompt dei comandi non restituisce il controllo dopo un comando **vsperfaspnetcmd**. È possibile usare l'opzione **/nowait** per imporre il ripristino del prompt dei comandi. Vedere [Uso dell'opzione /NoWait](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Per raccogliere statistiche sull'applicazione tramite il metodo di campionamento
 Il campionamento è il metodo di profilatura predefinito dello strumento **VSPerfASPNETCmd** e non è necessario specificarlo nella riga di comando. La riga di comando seguente consente di raccogliere statistiche sull'applicazione dall'applicazione Web specificata:

 **vsperfaspnetcmd**  *websiteUrl*

 Un esempio di *websiteUrl* ospitato su server locale potrebbe essere *http://localhost/MySite/default.aspx*. Un esempio di sito esterno è *http://www.contoso.com* . Per altre informazioni, vedere gli URL di esempio nella sezione [Per profilare un sito Web senza aprire un progetto in Visual Studio](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio).

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Per raccogliere dati di intervallo dettagliati tramite il metodo di strumentazione

Usare la riga di comando seguente per raccogliere dati di intervallo dettagliati da un'applicazione Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilata dinamicamente:

**vsperfaspnetcmd /trace**  *websiteUrl*

Se si desidera profilare in modo statico compilato . *dll* nell'applicazione Web, è necessario instrumentare i file usando lo strumento da riga di comando [VSInstr.](../profiling/vsinstr.md) Il comando vsperfaspnetcmd /trace includerà i dati dai file instrumentati.

## <a name="to-collect-net-memory-data"></a>Per raccogliere dati di memoria .NET

L'opzione **/Memory** consente di raccogliere dati sull'allocazione di oggetti nella memoria .NET ed è in grado di raccogliere dati sulla durata di tali oggetti. La raccolta di dati di allocazione è la modalità predefinita dell'opzione **/Memory** e non è necessario specificarla nella riga di comando.

 **vsperfaspnetcmd /memory** *websiteUrl*

 Usare il parametro **Lifetime** per raccogliere dati sulla durata degli oggetti oltre ai dati di allocazione:

 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 È inoltre possibile usare l'opzione **/Trace** per includere informazioni di intervallo dettagliate con i dati di memoria .NET:

 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Per raccogliere dati di interazione tra livelli

> [!WARNING]
> I dati di profilatura dell'interazione tra livelli possono essere raccolti usando qualsiasi edizione di Visual Studio, ma possono essere visualizzati solo in Visual Studio Enterprise.
>
> Per raccogliere dati TIP in Windows 8 o Windows Server 2012, è necessario usare l'opzione di strumentazione (**/trace**).

Per raccogliere dati di interazione tra livelli con dati di campionamento:

**vsperfaspnetcmd /tip** `websiteUrl`

Per raccogliere dati di interazione tra livelli con dati di strumentazione:

**vsperfaspnetcmd /trace /tip** *websiteUrl*

Per raccogliere dati di interazione tra livelli con dati di memoria .NET:

**vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_websiteUrl_

## <a name="use-the-nowait-option"></a>Usare l'opzione /NoWait

Per impostazione predefinita, il prompt dei comandi non restituisce il controllo dopo un comando **vsperfaspnetcmd**. È possibile usare l'opzione della sintassi seguente per imporre il ripristino del prompt dei comandi. È quindi possibile eseguire altre operazioni nella finestra del prompt dei comandi. Per terminare la profilatura, usare l'opzione **/shutdown** in un comando **vsperfaspnetcmd** distinto.

Per iniziare la profilatura:

**vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_

Per terminare la profilatura:

**vsperfaspnetcmd /shutdown** *websiteUrl*

## <a name="additional-options"></a>Opzioni aggiuntive

È possibile aggiungere una qualsiasi delle opzioni seguenti ai comandi elencati in precedenza in questa sezione, ad eccezione del comando **vsperfaspnetcmd /shutdown**.

|Opzione|Descrizione|
|------------|-----------------|
|**/Output:**`VspFile`|Per impostazione predefinita, il file dei dati di profilatura (con estensione *vsp*) viene creato nella directory corrente con il nome file **PerformanceReport.vsp**. Usare l'opzione /output per specificare un percorso o un nome file diverso o entrambi.|
|**/PackSymbols:Off**|Per impostazione predefinita, VsPerfASPNETCmd incorpora simboli (nomi di funzione e di parametro e così via) nel file con estensione *vsp*. L'incorporamento di simboli può aumentare notevolmente le dimensioni del file di dati di profilatura. Se quando si analizzano i dati si ha accesso ai file con estensione *pdb* contenenti i simboli, usare l'opzione /packsymbols:off per disabilitare l'incorporamento dei simboli.|
