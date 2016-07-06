# Encrypt-Decrypt-Data
This functions will let you encrypt and decrypt data 

        // Encrypt
        public static string Encryptdata(string password)
        {
            if (!String.IsNullOrEmpty((password)))
            {
                var encode = Encoding.UTF8.GetBytes(password);
                var strmsg = Convert.ToBase64String(encode);
                return strmsg;
            }
            return String.Empty;
        }

        // Decrypt
        public static string Decryptdata(string encryptpwd)
        {
            var encodepwd = new UTF8Encoding();
            var decode = encodepwd.GetDecoder();
            var todecodeByte = Convert.FromBase64String(encryptpwd);
            int charCount = decode.GetCharCount(todecodeByte, 0, todecodeByte.Length);
            var decodedChar = new char[charCount];
            decode.GetChars(todecodeByte, 0, todecodeByte.Length, decodedChar, 0);
            var decryptpwd = new String(decodedChar);
            return decryptpwd;
        }
