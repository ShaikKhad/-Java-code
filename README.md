https://time.com/import java.io.*;
import java.net.URL;
import java.util.regex.*;

public class HtmlParser {
    public static void main(String[] args) throws IOException {
        String urlString = "https://time.com";
        
        URL url = new URL(urlString);
        BufferedReader reader = new BufferedReader(new InputStreamReader(url.openStream()));
        
        StringBuilder htmlContent = new StringBuilder();
        String line;
        while ((line = reader.readLine()) != null) {
            htmlContent.append(line);
        }
        reader.close();
        
        String storyPattern = "<h3 class=\"latest-stories__item-headline\">(.*?)</h3>";
        Pattern pattern = Pattern.compile(storyPattern);
        Matcher matcher = pattern.matcher(htmlContent.toString());
        
        int storyCount = 0;
        while (matcher.find() && storyCount < 6) {
            System.out.println("Story " + (storyCount + 1) + ": " + matcher.group(1));
            storyCount++;
        }
    }
}


import java.io.*;
import java.net.URL;
import java.util.regex.*;

public class SimpleHTMLParser {
    public static void main(String[] args) {
        try {
            String urlString = "https://time.com";
            
            URL url = new URL(urlString);
            BufferedReader reader = new BufferedReader(new InputStreamReader(url.openStream()));
            
            StringBuilder htmlContent = new StringBuilder();
            String line;
            while ((line = reader.readLine()) != null) {
                htmlContent.append(line);
            }
            reader.close();
            
            String storyPattern = "<h3 class=\"latest-stories__item-headline\">(.*?)</h3>";
            Pattern pattern = Pattern.compile(storyPattern);
            Matcher matcher = pattern.matcher(htmlContent.toString());
            
            int storyCount = 0;
            while (matcher.find() && storyCount < 6) {
                System.out.println("Story " + (storyCount + 1) + ": " + matcher.group(1));
                storyCount++;
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
