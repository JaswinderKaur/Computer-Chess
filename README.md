# Computer-Chess
Minimax code
package chessproject;

import static chessproject.Chess.game;

/**
 *
 * @author Jaswi
 */
public class MiniMax {
    private boolean white;
    
    public MiniMax() {
        super();
    }
    
    public MiniMax(Chess game) {
        super(game);
    }
    
    public MiniMax(Board board) {
        super(board);
    }
    
    public Move getReply(boolean white) {
    System.out.println("\n"+(white?"White":"Black") + " replies with "+toString());
        int dd = 0;
    minimax(white, dd);
        Move mm = null;
    return mm;
  }
    
    public void minimax(boolean white, int depth){
    this.white = white;
  	int val = 0;
  	if(this.white)
  	  val = Max(depth); // white moves first
  	else
  	  val = Min(depth); // black moves first
  }
    
     private int Max(int depth) {
  	if (depth == 0)
  		return estimate();
  	int best = -INFINITY;
  	Vector v = successors(true);
  	if (v!=null) { 
  	  int siz = v.size();
  	  while(v.size()>0) {
  	    Move mv = (Move)v.remove(0);
  	    mv.perform(board);
  	    int val = -Min(depth-1);
  	    if (val>best) {
  	      best = val;
  	      if (this.white) {
                    Move mm = mv; // Current choice of move
  	      }
  	    }
  	    mv.undo(board);
  	  }
  	}
  	return best;
  }
     
      private int Min(int depth) {
    if (depth == 0)
      return estimate();
    int best = -INFINITY;
    Vector v = successors(false);
  	if (v!=null) { 
  	  int siz = v.size();
  	  while(v.size()>0) {
  	    Move mv = (Move)v.remove(0);
  	    mv.perform(board);
  	    int val = -Max(depth-1);
  	    if (val>best) {
  	      best = val;
  	      if (!this.white) {
                    Move mm = mv; // Current choice of move
  	      }
  	    }
  	    mv.undo(board);
  	  }
  	}
  	return best;
  }
      
    public String toString() {
    return "Minimax";
  }
}
