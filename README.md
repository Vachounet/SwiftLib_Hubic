SwiftLib_Hubic
==============
Modded SwiftLib to work with [Hubic.com](https://hubic.com)

You first need a swift proxy for hubic. Ex.: [Hubic2SwiftGate](https://github.com/oderwat/hubic2swiftgate)

Needed key in .config :

    <add key="SwiftUrl" value="proxyURL" />
    <add key="User" value="proxyUser" />
    <add key="AuthKey" value="proxyPWD" />
    <add key="BoxFolder" value="c:\box" />
    <add key="DownloadFolder" value="c:\boxd" />
    

Code :

        static SwiftConfig cfg = new SwiftConfig();
        static SwiftClient client;
        
        private static void InitConfig()
        {
            cfg.Url = System.Configuration.ConfigurationManager.AppSettings.Get("SwiftUrl");
            cfg.User = System.Configuration.ConfigurationManager.AppSettings.Get("User");
            cfg.Authkey = System.Configuration.ConfigurationManager.AppSettings.Get("AuthKey");
            cfg.BoxFolder = System.Configuration.ConfigurationManager.AppSettings.Get("BoxFolder");
            cfg.DownloadFolder = System.Configuration.ConfigurationManager.AppSettings.Get("DownloadFolder");
        }

        // build Swift client using the authentication
        // information in the configuration file
        public static void BuildClient()
        {
            if (client == null || !client.IsAuthenticated())
            {
                client = new SwiftClient(cfg);
            }
        }        
        
