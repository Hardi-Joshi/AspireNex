# AspireNex
```java
import java.util.*;
public class ChatBot{
        private static final Set<String> GREETINGS = new HashSet<>(Arrays.asList("hi", "hello", "hey", "good morning", "good afternoon", "good evening", "greetings"));
        private static final Set<String> WORK = new HashSet<>(Arrays.asList("what","help", "work", "tasks", "to-do", "job", "assignment"));
        private static final Set<String> AFFIRMATIONS = new HashSet<>(Arrays.asList("yes","good","ok","fine", "sure", "okay", "alright", "yep", "nice","great"));
        private static final List<String> JOKES = Arrays.asList(
            "Why don't scientists trust atoms? Because they make up everything!",
            "Why did the scarecrow win an award? Because he was outstanding in his field!",
            "Why don't skeletons fight each other? They don't have the guts."
    );
    private static final List<String> STORIES = new ArrayList<>();
    public static void main(String[] args){
        Scanner in = new Scanner(System.in);
        String input;
        System.out.println("Hello! I am an AI Chatbot. How can I help you today?");
        while (true) {
            input = in.nextLine().toLowerCase();
            if (isGreeting(input)) {
                System.out.println("Hello! How are you doing today?");
            }else if (containsAny(input, WORK)) {
                System.out.println("What kind of work do you have today?");
                String ans = in.nextLine();
                System.out.println("Umm..it seems I might not be able to help u with that. Is there something else I can help with?");
                String nextans = in.nextLine();
                if(nextans.contains("no")){
                    System.out.println("I'm sorry I coudn't assist you today.");
                    break;
                }else {
                    System.out.println("Sure, let me know how else I can help.");
                }
            } else if (containsAny(input, AFFIRMATIONS)) {
                System.out.println("Great! How can I assist you further?");
            }else if (input.contains("how are you")) {
                System.out.println("I'm doing great! Thanks for asking. What about you?");
            }else if (input.contains("what is your name")) {
                System.out.println("I am a chatbot. You can call me ChatBot!");
            } else if (input.contains("what can you do")) {
                System.out.println("I can chat with you, answer simple questions, tell jokes, listen to your stories, and provide information. How can I assist?");
            }else if (input.contains("tell me a joke")) {
                tellJoke();
            } else if (input.contains("share a story") || input.contains("tell me a story")) {
                shareStory();
            } else if (input.contains("i have a story")){
                System.out.println("I'd love to hear your story! Please go ahead.");
                String story = in.nextLine();
                STORIES.add(story);
                System.out.println("Thanks for sharing your story!");
            } else if (input.contains("bye") || input.contains("exit")) {
                System.out.println("Goodbye! Have a nice day!");
                break;
            } else if (input.contains("what is the weather like")) {
                System.out.println("I'm not connected to the internet, but you can check your local weather app for the latest update.");
            } else if (input.contains("thank you") || input.contains("thanks")) {
                System.out.println("You're welcome! Is there anything else I can help with?");
            } else{
                System.out.println("I'm not sure I understand");
            }
        }
    }
    private static boolean isGreeting(String input) {
        return GREETINGS.stream().anyMatch(input::contains);
    }

    private static boolean containsAny(String input, Set<String> keywords) {
        return keywords.stream().anyMatch(input::contains);
    }

    private static void tellJoke() {
        Random rand = new Random();
        System.out.println(JOKES.get(rand.nextInt(JOKES.size())));
    }

    private static void shareStory() {
        Scanner sc= new Scanner(System.in);
        if (STORIES.isEmpty()) {
            System.out.println("I don't have any stories to share right now. Would you like to tell me one?");
            String response=sc.nextLine();
            if(response.contains("y")){
                System.out.println("Nice, let's hear it then.");
                String story = sc.nextLine();
                STORIES.add(story);
                System.out.println("Thanks for sharing your story!");
            }
        } else {
            Random rand = new Random();
            System.out.println("Here's a story someone shared with me: " + STORIES.get(rand.nextInt(STORIES.size())));
        }
    }

}
```
