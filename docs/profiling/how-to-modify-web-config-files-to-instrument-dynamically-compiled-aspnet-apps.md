---
title: Web.Config file - Instrumentare & profilo dinamico ASP.NET app
description: Informazioni su come usare il Visual Studio Strumenti di profilatura per raccogliere dati di temporizzazione e attività di memoria per un'applicazione Web compilata ASP.NET dinamicamente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 6243c342756c593cf39f32f52b6341414d201e2dea4f4fcf6f208e8362c12246
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368357"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Procedura: Modificare file Web.Config per instrumentare e profilare applicazioni Web ASP.NET compilate dinamicamente
È possibile usare il metodo di strumentazione degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per raccogliere dati di intervallo dettagliati, dati relativi all'allocazione di memoria .NET e dati di durata degli oggetti .NET da applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilate in modo dinamico.

 In questo argomento viene descritto come modificare il file *web.config* di configurazione per abilitare la strumentazione e la profilatura [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] delle applicazioni Web.

> [!NOTE]
> Non è necessario modificare il file *web.config* quando si usa il metodo di profilatura del campionamento o quando si vuole instrumentare un modulo precompilato. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]

 La radice di un *web.config* file è l'elemento **di** configurazione. Per instrumentare ed eseguire la profilatura di un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilata in modo dinamico, è necessario aggiungere o modificare gli elementi seguenti:

- Elemento **configuration/runtime/assemblyBinding/dependentAssembly** che identifica l'assembly Microsoft.VisualStudio.Enterprise.ASPNetHelper che controlla il profilo. L'elemento **dependentAssembly** contiene due elementi figlio: **assemblyIdentity** e **codeBase**.

- Elemento **configuration/system.web/compilation** che identifica il passaggio di compilazione post-elaborazione del profiler per l'assembly di destinazione.

- Due elementi **add** che identificano il percorso degli strumenti di profilatura aggiunti alla sezione **configuration/appSettings**.

  È consigliabile creare una copia del file *web.config* originale che è possibile usare per ripristinare la configurazione dell'applicazione.

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Per aggiungere l'assembly ASPNetHelper come elemento configuration/runtime/assemblyBinding/dependentAssembly

1. Se necessario, aggiungere l'elemento **runtime** come elemento figlio dell'elemento **configuration**; in caso contrario, andare al passaggio successivo.

    L'elemento **runtime** non contiene attributi. L'elemento **configuration** può avere un solo elemento **runtime** figlio.

2. Se necessario, aggiungere l'elemento **assemblyBinding** come elemento figlio dell'elemento **runtime**; in caso contrario, andare al passaggio successivo.

    L'elemento **runtime** può avere un solo elemento **assemblyBinding** figlio.

3. Aggiungere il nome e il valore di attributo riportati di seguito all'elemento **assemblyBinding**:

   | Nome attributo | Valore dell'attributo |
   |----------------|--------------------------------------|
   | **Xmlns** | **urn:schemas-microsoft-com:asm.v1** |

4. Aggiungere un elemento **dependentAssembly** come elemento figlio dell'elemento **assemblyBinding**.

    L'elemento **dependentAssembly** non contiene attributi.

5. Aggiungere un elemento **assemblyIdentity** come elemento figlio dell'elemento **dependentAssembly**.

6. Aggiungere i nomi e i valori di attributo riportati di seguito all'elemento **assemblyIdentity**:

   | Nome attributo | Valore dell'attributo |
   |--------------------| - |
   | **nome** | **Microsoft.VisualStudio.Enterprise.ASPNetHelper** |
   | **PublicKeyToken** | **b03f5f7f11d50a3a** |
   | **Impostazioni cultura** | **Neutro** |

7. Aggiungere un elemento **codeBase** come elemento figlio dell'elemento **dependentAssembly**.

8. Aggiungere i nomi e i valori di attributo riportati di seguito all'elemento **codeBase**:

   |Nome attributo|Valore dell'attributo|
   |--------------------|---------------------|
   |**version**|**10.0.0.0**|
   |**href**|`PathToASPNetHelperDll`|

    `PathToASPNetHelperDll` è l'URL del file di Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene installato nel percorso predefinito, il valore **href** sarà `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`.

```xml
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"
                    />
                    <codeBase
                        version="10.0.0.0"
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"
                    />
                </dependentAssembly>
            </assemblyBinding>
        </runtime>
```

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Per aggiungere il passaggio di post-elaborazione del profiler all'elemento configuration/system.web/compilation

1. Se necessario, aggiungere l'elemento **system.web** come elemento figlio dell'elemento **configuration**; in caso contrario, andare al passaggio successivo.

     L'elemento **system.web** non contiene attributi. L'elemento **configuration** può avere un solo elemento **system.web** figlio.

2. Se necessario, aggiungere l'elemento **compilation** come elemento figlio dell'elemento **system.web**; in caso contrario, andare al passaggio successivo.

     L'elemento **system.web** può avere un solo elemento **compilation** figlio.

3. Rimuovere qualsiasi attributo esistente dall'elemento **compilation** e aggiungere il nome e il valore di attributo seguenti:

    |Nome attributo|Valore dell'attributo|
    |--------------------|---------------------|
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|

```xml
    <configuration>
        <runtime>
        . . .
        </runtime>
        <system.web>
            <compilation
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,
                    Version=10.0.0.0,
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            />
        </system.web>
    <configuration>
```

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Per aggiungere le impostazioni del percorso del profiler all'elemento configuration/appSettings

1. Se necessario, aggiungere l'elemento **appSettings** come elemento figlio dell'elemento **configuration**; in caso contrario, andare al passaggio successivo.

    L'elemento **appSettings** non contiene attributi. L'elemento **configuration** può avere un solo elemento **appSettings** figlio.

2. Aggiungere un elemento **add** come elemento figlio dell'elemento **appSettings**.

3. Aggiungere i nomi e i valori di attributo riportati di seguito all'elemento **add**:

   | Nome attributo | Valore dell'attributo |
   |----------------| - |
   | **key** | **Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation** |
   | **value** | `PerformanceToolsFolder` **\VSInstr.Exe** |

4. Aggiungere un altro elemento **add** come elemento figlio dell'elemento **appSettings**.

5. Aggiungere i nomi e i valori di attributo riportati di seguito a questo elemento **add**:

   |Nome attributo|Valore dell'attributo|
   |--------------------|---------------------|
   |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|
   |**value**|`PerformanceToolsFolder`|

    `PerformanceToolsFolder` è il percorso dei file eseguibili del profiler. Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

```xml
    <configuration>
        <runtime>
        . . .
        </runtime>
        . . .
        <system.web>
        </system.web>
        <appSettings>
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
        />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>
```

## <a name="example"></a>Esempio
 Di seguito è riportato un file *web.config* che consente la strumentazione e la profilatura di applicazioni [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web compilate dinamicamente. In questo esempio si presuppone che non vi siano state altre impostazioni nel file prima della modifica.

```xml
<?xml version="1.0"?>
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"
                    />
                    <codeBase
                        version="10.0.0.0"
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"
                    />
                </dependentAssembly>
            </assemblyBinding>
        </runtime>
        <system.web>
            <compilation
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,
                    Version=10.0.0.0,
                    Culture=neutral,
                    PublicKeyToken=b03f5f7f11d50a3a"
            />
        </system.web>
        <appSettings>
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
            />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>

```

## <a name="see-also"></a>Vedi anche
- [Procedura: Instrumentare un'applicazione ASP.NET dinamica e raccogliere dati di intervallo dettagliati](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)
- [Procedura: Instrumentare un'applicazione ASP.NET compilata dinamicamente e raccogliere dati di memoria](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)
