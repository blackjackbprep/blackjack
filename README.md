import java.util.List;
import java.util.ArrayList;
import java.util.Random;


public class Deck {

    private List<Card> cards;
    private int size;
    private int saveSize;

    public Deck(String[] ranks, String[] suits, int[] values) {
        cards = new ArrayList<Card>();
        for(int i = 0; i < ranks.length; i++){
            for(String suitString : suits){
                cards.add(new Card(ranks[i], suitString, values[i]));
            }
        }
        size = cards.size();
        saveSize = size;
    }


    public boolean isEmpty() {
        return size == 0;
    }


    public int size() {
        return size;
    }


    public void shuffle(){
        Card [] shuffled = new Card[52];
        Random r = new Random();
        int currentRand;
        for(int i = 0; i < shuffled.length; i++){
            int randNum = r.nextInt(cards.size());
            currentRand = randNum;
            shuffled[i] = cards.get(currentRand);
            cards.remove(currentRand);

        }
        for(int i = 0; i < shuffled.length; i++) {
            cards.add(shuffled[i]);
        }
    }

    public Card deal() {

    }

    @Override
    public String toString() {
        String rtn = "size = " + size + "\nUndealt cards: \n";

        for (int k = size - 1; k >= 0; k--) {{

    }
            rtn = rtn + cards.get(k);
            if (k != 0) {
                rtn = rtn + ", ";
            }
            if ((size - k) % 2 == 0) {
                // Insert carriage returns so entire deck is visible on console.
                rtn = rtn + "\n";
            }
        }

        rtn = rtn + "\nDealt cards: \n";
        for (int k = cards.size() - 1; k >= size; k--) {
            rtn = rtn + cards.get(k);
            if (k != size) {
                rtn = rtn + ", ";
            }
            if ((k - cards.size()) % 2 == 0) {
                // Insert carriage returns so entire deck is visible on console.
                rtn = rtn + "\n";
            }
        }

        rtn = rtn + "\n";
        return rtn;
    }
}
