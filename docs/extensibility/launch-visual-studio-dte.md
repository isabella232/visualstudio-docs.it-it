---
title: Avviare Visual Studio tramite DTE
titleSuffix: ''
ms.date: 04/26/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 399f98964dca29eccfd7d3c2bb691205f373a3b3
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747008"
---
# <a name="launch-visual-studio-using-dte"></a>Avviare Visual Studio tramite DTE

A partire da Visual Studio 2017, il meccanismo per avviare Visual Studio usando DTE è diverso per l'avvio delle versioni precedenti di Visual Studio. Questa modifica è necessaria perché Visual Studio 2017 e versioni successive supporta side-by-side le installazioni della maggior parte delle versioni (ad esempio, è possibile avere un'anteprima e una versione di rilascio installato side-by-side).

Il resto di questo articolo illustra il codice che è possibile usare per avviare Visual Studio 2019 usando DTE.

## <a name="set-up-the-project"></a>Configurare il progetto

Per visualizzare il codice che esegue l'applicazione in azione, creare un progetto seguendo questa procedura.

1. Creare una nuova **App Console** progetti per .NET Framework.

2. Installare il [Microsoft.VisualStudio.Setup.Configuration.Interop](https://www.nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop/) NuGet pacchetti e aggiungere un riferimento all'assembly.

3. Aggiungere un riferimento a EnvDTE.

4. Incollare il [esempio di codice](#example-code) che segue nel *Program.cs* file.

5. Premere **F5** per eseguire il programma. Si dovrebbe vedere Visual Studio 2019 aperti prima che il programma viene chiuso.

## <a name="example-code"></a>codice di esempio

```csharp
using Microsoft.VisualStudio.Setup.Configuration;
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.IO;
using System.Linq;
using System.Runtime.InteropServices;
using System.Runtime.InteropServices.ComTypes;
using System.Threading;

namespace ConsoleLauncherApp
{
    class Program
    {
        static void Main(string[] args)
        {
            EnvDTE.DTE dte = LaunchVsDte(isPreRelease: false);

            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateMaximize;
            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateMinimize;
            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateNormal;
            dte.Quit();
        }

        private static EnvDTE.DTE LaunchVsDte(bool isPreRelease)
        {
            ISetupInstance setupInstance = GetSetupInstance(isPreRelease);
            string installationPath = setupInstance.GetInstallationPath();
            string executablePath = Path.Combine(installationPath, @"Common7\IDE\devenv.exe");
            Process vsProcess = Process.Start(executablePath);
            string runningObjectDisplayName = $"VisualStudio.DTE.16.0:{vsProcess.Id}";

            IEnumerable<string> runningObjectDisplayNames = null;
            object runningObject;
            for (int i = 0; i < 60; i++)
            {
                try
                {
                    runningObject = GetRunningObject(runningObjectDisplayName, out runningObjectDisplayNames);
                }
                catch
                {
                    runningObject = null;
                }

                if (runningObject != null)
                {
                    return (EnvDTE.DTE)runningObject;
                }

                Thread.Sleep(millisecondsTimeout: 1000);
            }

            throw new TimeoutException($"Failed to retrieve DTE object. Current running objects: {string.Join(";", runningObjectDisplayNames)}");
        }

        private static object GetRunningObject(string displayName, out IEnumerable<string> runningObjectDisplayNames)
        {
            IBindCtx bindContext = null;
            NativeMethods.CreateBindCtx(0, out bindContext);

            IRunningObjectTable runningObjectTable = null;
            bindContext.GetRunningObjectTable(out runningObjectTable);

            IEnumMoniker monikerEnumerator = null;
            runningObjectTable.EnumRunning(out monikerEnumerator);

            object runningObject = null;
            List<string> runningObjectDisplayNameList = new List<string>();
            IMoniker[] monikers = new IMoniker[1];
            IntPtr numberFetched = IntPtr.Zero;
            while (monikerEnumerator.Next(1, monikers, numberFetched) == 0)
            {
                IMoniker moniker = monikers[0];

                string objectDisplayName = null;
                try
                {
                    moniker.GetDisplayName(bindContext, null, out objectDisplayName);
                }
                catch (UnauthorizedAccessException)
                {
                    // Some ROT objects require elevated permissions.
                }

                if (!string.IsNullOrWhiteSpace(objectDisplayName))
                {
                    runningObjectDisplayNameList.Add(objectDisplayName);
                    if (objectDisplayName.EndsWith(displayName, StringComparison.Ordinal))
                    {
                        runningObjectTable.GetObject(moniker, out runningObject);
                        if (runningObject == null)
                        {
                            throw new InvalidOperationException($"Failed to get running object with display name {displayName}");
                        }
                    }
                }
            }

            runningObjectDisplayNames = runningObjectDisplayNameList;
            return runningObject;
        }

        private static ISetupInstance GetSetupInstance(bool isPreRelease)
        {
            return GetSetupInstances().First(i => IsPreRelease(i) == isPreRelease);
        }

        private static IEnumerable<ISetupInstance> GetSetupInstances()
        {
            ISetupConfiguration setupConfiguration = new SetupConfiguration();
            IEnumSetupInstances enumerator = setupConfiguration.EnumInstances();

            int count;
            do
            {
                ISetupInstance[] setupInstances = new ISetupInstance[1];
                enumerator.Next(1, setupInstances, out count);
                if (count == 1 &&
                    setupInstances != null &&
                    setupInstances.Length == 1 &&
                    setupInstances[0] != null)
                {
                    yield return setupInstances[0];
                }
            }
            while (count == 1);
        }

        private static bool IsPreRelease(ISetupInstance setupInstance)
        {
            ISetupInstanceCatalog setupInstanceCatalog = (ISetupInstanceCatalog)setupInstance;
            return setupInstanceCatalog.IsPrerelease();
        }

        private static class NativeMethods
        {
            [DllImport("ole32.dll")]
            public static extern int CreateBindCtx(uint reserved, out IBindCtx ppbc);

            [DllImport("ole32.dll")]
            public static extern void GetRunningObjectTable(int reserved, out IRunningObjectTable prot);
        }
    }
}
```

## <a name="see-also"></a>Vedere anche

- [Locate Visual Studio](locating-visual-studio.md)
- [Procedura dettagliata: Accedere all'oggetto DTE da un'estensione dell'editor](walkthrough-accessing-the-dte-object-from-an-editor-extension.md)
