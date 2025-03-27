class IterativeDeepening:
    def __init__(self):
        self.path = []
        self.rows = 0
        self.cols = 0
        self.depth = 0
        self.maxDepth = 0
        self.goalFound = False
        self.maze = []
        self.start = (0, 0)
        self.target = (0, 0)
        self.directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]  # up, down, left, right

    def read_input(self):
      
        self.rows, self.cols = map(int, input().split())
        
       
        self.maze = []
        for _ in range(self.rows):
            self.maze.append(list(map(int, input().split())))
        
        
        self.start = tuple(map(int, input().split()))
        self.target = tuple(map(int, input().split()))

    def depth_limited_search(self, current, visited, current_depth):
        if current == self.target:
            self.goalFound = True
            return True
        
        if current_depth >= self.maxDepth:
            return False
        
        for direction in self.directions:
            next_row = current[0] + direction[0]
            next_col = current[1] + direction[1]
            
          
            if (0 <= next_row < self.rows and 0 <= next_col < self.cols and 
                self.maze[next_row][next_col] == 0 and 
                (next_row, next_col) not in visited):
                
                visited.add((next_row, next_col))
                self.path.append((next_row, next_col))
                
                found = self.depth_limited_search((next_row, next_col), visited, current_depth + 1)
                if found:
                    return True
                
               
                self.path.pop()
                visited.remove((next_row, next_col))
        
        return False

    def iterative_deepening(self):
        max_possible_depth = self.rows * self.cols  
        
        for self.maxDepth in range(1, max_possible_depth + 1):
            visited = set()
            visited.add(self.start)
            self.path = [self.start]
            
            if self.depth_limited_search(self.start, visited, 0):
                print(f"Path found at depth {self.maxDepth} using IDDFS")
                print("Traversal Order:", self.path)
                return
        
        print(f"Path not found at max depth {max_possible_depth} using IDDFS")

if __name__ == "__main__":
    try:
        iddfs = IterativeDeepening()
        iddfs.read_input()
        iddfs.iterative_deepening()
    except ValueError:
        print("Wrong Input format")
