;; The first three lines of this file were inserted by DrRacket. They record metadata
;; about the language level of this file in a form that our tools can easily process.
#reader(lib "htdp-beginner-reader.ss" "lang")((modname compound_data_quiz) (read-case-sensitive #t) (teachpacks ()) (htdp-settings #(#t constructor repeating-decimal #f #t none #f () #f)))
(require 2htdp/image)
(require 2htdp/universe)

;; Growing square

;; Constants

(define WIDTH  400)
(define HEIGHT 400)

(define CTR-X (/ WIDTH 2))
(define CTR-Y (/ HEIGHT 2))

(define DEFAULT-SIZE 20)
(define SIZE-GROWTH 3)  

(define MTS (rectangle WIDTH HEIGHT "solid" "white"))

;; ============
;; Data Definitions

(define-struct ss (x y s))
;; SquareState is (make-ss Number Number Natural)
;; interp. The state of a square
;;  x, y - coordinates
;;  s - size (width and height)

(define SS1 (make-ss 50 100 DEFAULT-SIZE))
(define SS2 (make-ss 5 10 25))

#;
(define (fn-for-square-state ss)
  (... (ss-x ss)
       (ss-y ss)
       (ss-s ss)))

;; Template rules used:
;; - compound: 3 fields

;; ===========
;; Functions

;; SquareState -> SquareState
;; run the animation, starting with initial square state ss.
;; start with (main (make-ss CTR-X CTR-Y DEFAULT-SIZE))
;; <no tests for main functions>

(define (main bs)
  (big-bang bs
    (on-tick next-ss)
    (to-draw render-ss)
    (on-mouse  new-ss)))

;; SquareState -> SquareState
;; increase size by SIZE-GROWTH
(check-expect (next-ss (make-ss 0 0 DEFAULT-SIZE))
              (make-ss 0 0 (+ DEFAULT-SIZE SIZE-GROWTH)))

(define (next-ss ss)
  (make-ss
   (ss-x ss)
   (ss-y ss)
   (+ (ss-s ss) SIZE-GROWTH)
   )
  )

;; SquareState -> Image
;; produces the ss at the appropriate location and with the appropriate size
(check-expect (render-ss (make-ss 0 0 DEFAULT-SIZE))
              (place-image (rotate 45 (rectangle DEFAULT-SIZE DEFAULT-SIZE "solid"  "purple")) 0 0 MTS))

(define (render-ss ss)
  (place-image (rotate 45 (rectangle (ss-s ss) (ss-s ss) "solid"  "purple")) (ss-x ss) (ss-y ss) MTS)
  )

;; SquareState KeyEvent -> SquareState
;; creates a new square at the location of the mouse when clicked, removing the old square
(check-expect (new-ss (make-ss 0 0 DEFAULT-SIZE) 15 15 "button-up")
              (make-ss 15 15 DEFAULT-SIZE))
(check-expect (new-ss (make-ss 0 0 DEFAULT-SIZE) 15 15 "button-down")
              (make-ss 0 0 DEFAULT-SIZE))

(define (new-ss ss mx my mouse)
  (cond
    [(mouse=? "button-up" mouse) (make-ss mx my DEFAULT-SIZE)]
    [else ss]
    )
  )









