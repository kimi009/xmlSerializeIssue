# xmlSerializeIssue
xmlSerialize Issue
#region XML转义字符处理

        /// <summary>

        /// XML转义字符处理

        /// </summary>

        public static string ConvertXml(string xml)

        {



            xml = (char)1 + xml;   //为了避免首字母为要替换的字符，前加前缀



            for (int intNext = 0; true; )

            {

                int intIndexOf = xml.IndexOf("&", intNext);

                intNext = intIndexOf + 1;  //避免&被重复替换

                if (intIndexOf <= 0)

                {

                    break;

                }

                else

                {

                    xml = xml.Substring(0, intIndexOf) + "&amp;" + xml.Substring(intIndexOf + 1);

                }

            }



            for (; true; )

            {

                int intIndexOf = xml.IndexOf("<");

                if (intIndexOf <= 0)

                {

                    break;

                }

                else

                {

                    xml = xml.Substring(0, intIndexOf) + "&lt;" + xml.Substring(intIndexOf + 1);

                }

            }



            for (; true; )

            {

                int intIndexOf = xml.IndexOf(">");

                if (intIndexOf <= 0)

                {

                    break;

                }

                else

                {

                    xml = xml.Substring(0, intIndexOf) + "&gt;" + xml.Substring(intIndexOf + 1);

                }

            }



            for (; true; )

            {

                int intIndexOf = xml.IndexOf("\"");

                if (intIndexOf <= 0)

                {

                    break;

                }

                else

                {

                    xml = xml.Substring(0, intIndexOf) + "&quot;" + xml.Substring(intIndexOf + 1);

                }

            }



            return xml.Replace(((char)1).ToString(), "");



        }

        #endregion
