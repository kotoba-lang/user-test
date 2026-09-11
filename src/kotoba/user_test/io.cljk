(ns kotoba.user-test.io
  "Explicit EDN I/O for the CLI. Core user-test evaluation remains pure."
  (:require [clojure.edn :as edn]
            [clojure.java.io :as io]))

(defn read-edn [path]
  (with-open [reader (java.io.PushbackReader. (io/reader path))]
    (edn/read {:eof nil} reader)))

(defn write-edn! [path value]
  (let [file (io/file path)]
    (when-let [parent (.getParentFile file)] (.mkdirs parent))
    (spit file (str (pr-str value) "\n"))
    (.getCanonicalPath file)))
